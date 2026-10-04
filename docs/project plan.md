# Project Plan

## Project Goal

The goal of the project is to develop an autonomous game agent implemented as a C++ DLL.

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

## Strategy

- **Explore intelligently** — move through unknown routes and avoid wasting time revisiting already explored dead ends.

- **Build a map while moving** — store paths, intersections, obstacles, flags, bases, and useful shortcuts.

- **Choose targets intelligently** — when a flag is found, decide whether it is worth collecting immediately or whether another known flag is better.

- **Return using the best route** — short route on the known map to return to your base.

- **Continue from useful unexplored areas** — after depositing a flag, don’t restart exploration blindly; continue from the most promising unknown region.

- **Adapt when the map changes** — if a route becomes blocked or dangerous, recalculate instead of stubbornly following the old path.

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
- Can easily be run again if a route becomes blocked