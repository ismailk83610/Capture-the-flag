# Project Goal

The goal of the project is to develop an autonomous game agent implemented as a C++ DLL.
The API for the game will be provided.

The DLL will be loaded by a host game application.

The agent should be able to:

- explore the environment
- locate flags
- move toward flags
- capture flags
- return flags to the home/base position
- avoid obstacles
- react to other players
- possibly use strategic behaviour to slow down opponents

## Algorithms choosen

1. **Exploration** - Frontier + Information Gain

We chose Frontier-Based Exploration with Information Gain because the agent starts with an unknown map and needs to discover it efficiently.

Frontier exploration identifies the boundary between known and unknown areas.
 Information Gain then helps choose which frontier is most useful to visit next.

Why this is better than simple alternatives:
- Better than random movement because the agent does not waste time wandering.
- Better than plain DFS because DFS may go very deep into one branch and spend time backtracking.
- Better than nearest-frontier-only because the nearest frontier may reveal very little new information.
- Information Gain helps balance travel distance vs expected new map knowledge.

2. **Map Storage** - Dynamic Map Storage

We chose a dynamic graph-based map because the environment may change during the game.
The graph stores:

- Nodes: intersections, bases, flags, dead ends, important positions
- Edges: routes between nodes
- Edge information: distance, blocked/open state, risk, last checked time

Why this is better than a static map:
- A static map assumes the environment never changes.
- In your game, another DLL may block a route or modify the environment.
- A dynamic map can update an edge from: OPEN to Blocked.

3. **Navigation and Return** - A*

Why A* is better than some alternatives:
- Better than BFS because BFS does not handle weighted routes well.
- Better than DFS because DFS does not guarantee the shortest route.
- Often faster than Dijkstra because A* uses the destination direction to guide the search.
- Works very well with a graph map.
- Can easily be run again if a route becomes 

## Proposed Agent Strategy

**Step 1: Initialize the Agent** 
- The agent starts at its initial position.
- Initialize the internal map memory.
- Initialize the agent's position-tracking system.
- Initially, the environment is considered unknown.
- Initialize the visited-cell information and visit counts.
- Prepare storage for the enemy flag and own home locations.

**Step 2: Start Exploring the Environment**
- The agent observes its surroundings using the 5 × 5 view provided by the API.
- Detect nearby walls, free cells, flags, and target locations.
- Update the internal map using the observed information.
- Begin exploring the unknown environment.

    ***Algorithm: Frontier-Based Exploration.***

**Step 3: Prefer Less-Explored Areas** 
- The agent should avoid visiting the same areas unnecessarily.
- Give priority to unexplored or less-explored regions.
- Identify frontier cells between known and unknown areas.
- Estimate the information gain of each frontier.
- Consider the travel distance to each frontier.
- Select the most promising frontier as the next destination.
- Previously visited paths can be reused when necessary to reach unexplored areas.

**Algorithms and techniques:**

        - Frontier Exploration

        - Information Gain

        - Visit Count / Visited-Cell Penalty

**Step 4: Store and Update the Map** 
- While moving, the agent continuously records the observed environment.
- Store free cells, walls, unknown cells, and visited locations.
- Keep track of the number of visits to each cell.
- Record important positions, especially the enemy flag and own home.
- If new information differs from the stored map, update the map.
- Keep temporary obstacles, such as the enemy agent, separate from permanent walls.

    ***Method: Dynamic Occupancy Grid Map.***

**Step 5: Navigate to Exploration Destinations**
- After selecting a frontier, calculate a route toward it.
- Use the stored map to avoid known walls.
- Follow the calculated path.
- Previously visited cells may be used if they provide a useful route.
- If the planned path becomes blocked, update the map and calculate another route.

    ***Algorithm: A* Pathfinding with Dynamic Replanning.***

**Step 6: Detect Important Locations** 
- During exploration, the agent searches for two important locations:
- Enemy Flag: The location where the enemy flag can be collected.
- Own Home: The location where the captured enemy flag must be delivered.
- Store both locations independently.
- Either location may be discovered first.
- Do not assume the starting position is the home position

**Step 7: If the Agent Finds Home First**
- Store the home location in the internal map.
- Continue exploring to locate the enemy flag.
- When the enemy flag is found, navigate to it and attempt pickup.
- After successfully capturing the flag, use A* to calculate an efficient route to the stored home location.
- Navigate to home and deliver the captured flag          

***Algorithms:***
- Dynamic Map Storage
- Frontier + Information Gain
- A* Pathfinding
***Step 8: If the Agent Finds the Enemy Flag First***
- Store the enemy flag location.
- Navigate to the flag if necessary.
- Attempt to pick up the enemy flag.
- If the home location is still unknown, continue exploration while carrying the flag, provided the game rules allow it.
- Prefer unexplored regions using Frontier Exploration and Information Gain.
- Once the home location is found, calculate a route to it using A*.
- Navigate to home and deliver the captured flag.

***Algorithms:***
- Frontier + Information Gain
- Dynamic Map Storage
- A* Pathfinding

***Step 9: Handle Dynamic Obstacles and Map Changes***
- Continuously observe the surroundings while navigating.
- If a newly discovered obstacle blocks the planned route, update the internal map.
- Calculate an alternative route using A*.
- Continue toward the destination.
- Avoid treating temporary enemy occupancy as a permanent wall.

***Method: Dynamic Replanning with A*.***

***Step 10: Deliver the Enemy Flag***
- When the agent reaches its own home (delivery target), request the flag drop action through the API.
- Verify delivery according to the host's game rules.
- Complete the mission once successful delivery is confirmed.

***Agent Decision-Making States***
- The agent will use a ***Finite State Machine*** to control its behavior.
    - EXPLORE: Search unexplored regions using Frontier Exploration and Information Gain.
    - GO_TO_FLAG: Navigate toward the detected enemy flag using A*.
    - PICK_UP_FLAG: Attempt to capture the enemy flag.
    - FIND_HOME: Continue exploring if the home location is unknown.
    - GO_TO_HOME: Calculate and follow a route to the home location using A*.
    - DELIVER_FLAG: Request delivery of the captured enemy flag.
    - DONE: Mission completed successfully.
- The state changes according to the agent's current objective and available information.



