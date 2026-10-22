
# Project Definition

## 1. Introduction

This document presents the initial project definition for the combined Software and Research Project.


The agent will be developed in C++ and compiled into a Dynamic Link Library (DLL), which will communicate with the game host through the provided Agent API.

As the project follows an Agile development approach, this initial definition may be refined based on technical findings and experimental results.

---

## 2. Problem Statement

The Capture the Flag game environment requires an autonomous agent to navigate a map, locate an opponent's flag, capture it, and return it to its home base.

The agent initially has limited knowledge of the environment and must make navigation decisions based on information obtained through the provided Agent API.

The main challenge is to develop an agent capable of exploring an unknown environment efficiently while maintaining an internal representation of the discovered map.

During exploration, the agent should avoid unnecessary repeated visits to previously explored locations. However, previously visited routes may be reused when necessary to reach a destination.

Once an opponent's flag is discovered, the agent must navigate toward the flag, capture it according to the game rules, and find a suitable route back to its home base.

Additional challenges may occur when the environment changes or previously accessible routes become blocked. The agent should recognize these changes and adapt its navigation strategy.

The software must operate within the technical restrictions imposed by the host application and the provided Agent API.

---

## 3. Project Objectives

### 3.1 Main Objective

The primary objective is to develop and evaluate an autonomous C++ agent capable of exploring an initially unknown Capture the Flag environment, locating an opponent's flag, capturing it, and returning it to the home base using suitable navigation algorithms.

### 3.2 Specific Objectives

The project aims to:

1. Understand the structure and functionality of the provided game host and Agent API.
2. Develop a compatible C++ Dynamic Link Library (DLL).
3. Implement an internal map representation to store information about the explored environment.
4. Track visited and unexplored locations during navigation.
5. Implement Frontier Exploration to identify suitable unexplored areas.
6. Investigate Information Gain to improve exploration target selection.
7. Implement the A* algorithm for pathfinding between known locations.
8. Implement flag detection, capture, and return behavior according to the game rules.
9. Update the stored map when new environmental information becomes available.
10. Recalculate paths when previously planned routes become invalid.
11. Organize agent behavior using a Finite State Machine (FSM).
12. Test and evaluate the agent under different game conditions.
13. Document the implementation, experimental results, and research findings.

---

## 4. Project Scope

### 4.1 In Scope

The following activities are included in the project:

- Development of the autonomous agent using C++.
- Compilation and integration of the agent as a DLL.
- Communication with the game environment through the Agent API.
- Implementation of basic movement and navigation.
- Development of internal map storage.
- Tracking explored and unexplored map locations.
- Implementation of Frontier Exploration and Information Gain.
- Implementation of A* pathfinding.
- Implementation of flag detection and handling.
- Development of return-to-base navigation.
- Dynamic map updates and alternative route planning.
- Finite State Machine for agent behavior management.
- Functional testing and performance evaluation.
- Documentation of software design and research findings.


## 5. Expected Results

The project is expected to produce the following deliverables:

### 5.1 Software Deliverables

1. A functional C++ autonomous Capture the Flag agent.
2. A compiled DLL compatible with the provided host.
3. An internal map representation for storing discovered environmental information.
4. An exploration component using Frontier Exploration and potentially Information Gain.
5. A pathfinding component based on the A* algorithm.
6. A behavior management component using a Finite State Machine.
7. Functionality for capturing a flag and returning to the home base.
8. A mechanism for handling changes in the map and replanning routes.


## 6. Functional Requirements

Functional requirements describe the operations and capabilities that the software must provide.

| ID | Functional Requirement | Priority |
|---|---|---|
| FR01 | The agent shall obtain available information about its current game state through the provided API. | High |
| FR02 | The agent shall identify accessible and blocked locations based on the observations available through the API. | High |
| FR03 | The agent shall maintain an internal map representation of the explored environment. | High |
| FR04 | The agent shall record visited locations and distinguish them from unexplored locations. | High |
| FR05 | The agent shall identify frontier locations between explored and unexplored regions. | High |
| FR06 | The agent should use Information Gain to support the selection of exploration targets. | Medium |
| FR07 | The agent shall select valid movement actions according to the game rules. | High |
| FR08 | The agent shall detect an opponent's flag when it becomes observable. | High |
| FR09 | The agent shall perform the required actions to capture the opponent's flag. | High |
| FR10 | The agent shall calculate navigation paths using the A* algorithm. | High |
| FR11 | The agent shall navigate toward its home base after capturing a flag. | High |
| FR12 | The agent shall update its internal map when new or changed environmental information is observed. | High |
| FR13 | The agent shall attempt alternative routes when an existing path becomes blocked. | High |
| FR14 | The agent shall manage different operating states using a Finite State Machine. | High |
| FR15 | The agent shall attempt to recover from navigation failures, including unreachable exploration targets. | Medium |

The requirements will be reviewed and refined after further analysis of the host application and Agent API.

---

## 7. Non-Functional Requirements

Non-functional requirements describe the quality, reliability, performance, and maintainability expectations of the software.

| ID | Category | Non-Functional Requirement |
|---|---|---|
| NFR01 | Performance | The agent shall make decisions within the execution-time limits specified by the host application. |
| NFR02 | Reliability | The agent shall operate without crashes or invalid memory access during normal gameplay. |
| NFR03 | Compatibility | The compiled DLL shall use the interface and binary format required by the host application. |
| NFR04 | Maintainability | The software shall be organized into modular and understandable C++ components. |
| NFR05 | Testability | Core components, including mapping and pathfinding, should support independent testing. |
| NFR06 | Navigation Efficiency | The agent should reduce unnecessary movement and repeated exploration. |
| NFR07 | Robustness | The agent shall handle blocked routes and unreachable destinations without unexpected termination. |
| NFR08 | Documentation | The source code, algorithms, technical decisions, and test results shall be documented. |
| NFR09 | Resource Efficiency | The agent shall operate within the memory and computational resource limits imposed by the host. |
| NFR10 | Adaptability | The software design should allow navigation algorithms and exploration strategies to be modified during development. |

Specific numerical performance thresholds will be established after verifying the host's limitations and conducting preliminary tests.


