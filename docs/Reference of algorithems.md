# Initial Algorithm Research

## 1. A* Search Algorithm

A* is a pathfinding algorithm used to find an efficient route from a starting point to a target.

It combines:

- the cost already travelled
- an estimate of the remaining distance to the target

Possible use in this project:

- finding the shortest path to a flag
- returning from a flag to the home/base position
- navigating around obstacles
- recalculating a path when the environment changes

### Advantages

- usually faster than Dijkstra when the target is known
- suitable for grid-based maps
- commonly used in games and robotics

### Disadvantages

- requires a suitable heuristic
- path recalculation may be necessary when obstacles or opponents move

---

## 2. Dijkstra's Algorithm

Dijkstra's algorithm finds the path with the lowest total cost.

Unlike simple shortest-path algorithms, it can handle different movement costs.

For example:

```text
Normal terrain = cost 1
Difficult terrain = cost 3
Dangerous area = cost 6
Enemy-controlled area = cost 10
```

Possible use in this project:

- choosing a safer route instead of only the shortest route
- avoiding dangerous areas
- calculating routes with different terrain costs

### Advantages

- guarantees the lowest-cost path
- supports weighted maps
- useful when some areas should be avoided

### Disadvantages

- explores more nodes than A*
- can be slower on large maps

---

## 3. Breadth-First Search (BFS)

Breadth-First Search checks positions level by level.

If all movements have the same cost, BFS can find the shortest path.

Possible use in this project:

- simple pathfinding
- finding the nearest reachable location
- testing basic map navigation

### Advantages

- simple to understand
- guarantees the shortest path when all movements have equal cost

### Disadvantages

- can search a large part of the map
- less efficient than A* when the destination is known

---

## 4. Depth-First Search (DFS)

Depth-First Search follows one path as far as possible before returning and trying another path.

Possible use in this project:

- maze-like exploration
- searching connected regions

### Advantages

- easy to implement
- useful for exploring branches

### Disadvantages

- does not guarantee the shortest path
- can waste time exploring long dead ends

---

## 5. Frontier-Based Exploration

Frontier-based exploration is useful when the complete map is not known.

The agent separates the world into:

- explored areas
- unexplored areas

A frontier is the border between known and unknown areas.

The agent chooses a frontier and moves toward it in order to discover new parts of the map.

Possible use in this project:

- searching for enemy flags
- discovering unknown parts of the map
- reducing repeated exploration of the same locations

A possible procedure is:

```text
Find unexplored frontier
        ↓
Choose a suitable frontier
        ↓
Use A* to travel there
        ↓
Explore new area
        ↓
Repeat
```

### Advantages

- systematic exploration
- avoids purely random movement
- works well together with A*

### Disadvantages

- requires storing information about explored areas
- may need a strategy to choose between several frontiers

---

## 6. Finite State Machine (FSM)

A Finite State Machine can control the overall behaviour of the agent.

The agent can be in one state at a time.

Possible states are:

```text
EXPLORE
SEARCH_FLAG
GO_TO_FLAG
CAPTURE_FLAG
RETURN_HOME
AVOID_ENEMY
DEFEND
```

Example:

```text
START
  ↓
EXPLORE
  ↓
Flag found?
  ├── No  → Continue exploring
  └── Yes → GO_TO_FLAG
                ↓
           CAPTURE_FLAG
                ↓
           RETURN_HOME
                ↓
              SCORE
```

Possible rules:

```text
If no flag is known:
    EXPLORE

If a flag is found:
    GO_TO_FLAG

If carrying a flag:
    RETURN_HOME

If an enemy blocks the route:
    AVOID_ENEMY
```

### Advantages

- simple structure
- easy to understand and debug
- good for controlling game behaviour

### Disadvantages

- can become complicated if too many states are added
- large FSMs may be difficult to maintain

---

## 7. Behavior Trees

Behavior Trees are another way to control decision-making.

They are commonly used in game AI.

Example:

```text
ROOT
 |
Has Flag?
 ├── Yes → Return Home
 └── No
      |
   Enemy Near?
    ├── Yes → Avoid Enemy
    └── No  → Search for Flag
```

Possible use in this project:

- handling complex behaviour
- combining attack, defence, exploration, and escape logic

### Advantages

- modular
- easy to extend
- suitable for larger AI systems

### Disadvantages

- more complex than an FSM
- may be unnecessary for the first version of the project

---

## 8. Potential Fields

Potential Field methods use attractive and repulsive forces.

For example:

```text
Flag     = attraction
Home     = attraction
Enemy    = repulsion
Obstacle = repulsion
```

The agent is pulled toward the target and pushed away from danger.

Example:

```text
          FLAG
            ↑
            ↑
         PLAYER
       ↙        ↘
   ENEMY       WALL
```

Possible use in this project:

- obstacle avoidance
- enemy avoidance
- smooth movement toward a target

### Advantages

- useful for local movement
- can produce smooth reactions
- suitable for avoiding nearby obstacles

### Disadvantages

- can get stuck in local minima
- not always reliable as the main pathfinding algorithm

---

## 9. Steering Behaviors

Steering behaviours are commonly used for movement in games.

Examples include:

```text
Seek
Flee
Avoid
Pursue
Evade
Arrive
Wander
```

Examples:

```text
PLAYER → → → FLAG
```

This is a `Seek` behaviour.

```text
ENEMY → PLAYER → → →
```

This is a `Flee` or `Evade` behaviour.

Possible use in this project:

- moving toward a flag
- escaping an enemy
- avoiding obstacles
- following moving targets

Steering behaviours could be combined with A* pathfinding.

---

