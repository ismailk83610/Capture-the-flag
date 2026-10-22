
# Project Management

## 1. Introduction

The agent will be implemented in C++ and compiled as a Dynamic Link Library (DLL), which will interact with the provided game host through the Agent API.

The project involves software development, algorithm research, implementation, testing, and performance evaluation.

To organize and manage these activities, an **Agile development approach supported by Kanban** has been selected.

A **Gantt chart** will also be prepared to represent the project schedule, major activities, and milestones.

---

## 2. Selected Project Management Approach

The following approaches and tools have been selected:

| Component | Selected Approach | Purpose |
|---|---|---|
| Software Development Methodology | Agile | Incremental development, testing, and continuous improvement |
| Task Management | Kanban | Visualizing, organizing, and tracking project tasks |
| Project Scheduling | Gantt Chart | Planning activities, timelines, dependencies, and milestones |


The combination of Agile and Kanban provides flexibility while maintaining a structured development process.

---

## 3. Selection of Agile Methodology

### 3.1 What is Agile?

Agile is an iterative and incremental approach to software development.

Instead of developing the entire software system before testing, the project is divided into smaller development activities.

Each development iteration involves:

1. Planning a feature or improvement.
2. Implementing the required functionality.
3. Testing the implementation.
4. Evaluating the results.
5. Improving the software based on the findings.

This process is repeated throughout the project.

### 3.2 Why Agile Was Selected

Agile was selected for the following reasons:

**1. Experimental Nature of the Project**

The project includes research and implementation of navigation and exploration algorithms.

Algorithms such as Frontier Exploration, Information Gain, and A* Pathfinding must be implemented and tested to evaluate their suitability.

Their performance cannot be completely predicted before experimentation.

Agile allows algorithms and implementation decisions to be modified based on testing results.

**2. Incremental Software Development**

The agent can be developed in smaller functional components.

For example:

- Basic agent movement and API integration.
- Internal map representation and storage.
- Exploration using Frontier Exploration.
- Path planning using A*.
- Flag detection, capture, and return.
- Dynamic map updates and route recovery.

Each component can be tested before additional functionality is introduced.

**3. Flexibility to Handle Changes**

During development, new technical limitations or unexpected problems may be identified.

For example, the agent may encounter situations where an existing route becomes blocked or an exploration strategy performs inefficiently.

Agile supports revising the implementation based on these findings.

**4. Continuous Testing and Improvement**

Testing will be performed throughout development rather than only at the end.

This helps identify errors earlier and allows improvements to be introduced incrementally.

**5. Suitable for Software and Research Activities**

The project combines software engineering with experimental research.

Agile supports continuous interaction between research, implementation, testing, and evaluation.

## 4. Selection of Kanban

### 4.1 What is Kanban?

Kanban is a visual task management method used to organize and monitor work.

Tasks are represented as cards and move through different workflow stages as work progresses.

The planned workflow consists of:

**Backlog → To Do → In Progress → Testing → Done**

This makes it easier to identify:

- Tasks that have not yet been started.
- Tasks currently being developed.
- Tasks awaiting testing.
- Completed tasks.
- Activities that require additional attention.

### 4.2 Why Kanban Was Selected

**1. Suitable for Individual Project Development**

The project is being carried out individually.

Kanban provides a lightweight way to organize development activities without requiring formal team roles or frequent meetings.

**2. Simple Progress Tracking**

Kanban provides a clear overview of the current project status.

Tasks can be moved between workflow stages as progress is made.

**3. Flexible Task Prioritization**

Tasks may need to be reprioritized based on implementation challenges, experimental results, or changes in project requirements.

Kanban allows this flexibility.

**4. Continuous Workflow**

Unlike Scrum, Kanban does not require fixed-length Sprints.

Tasks can be selected and completed continuously based on their priority and the available capacity.

**5. Integration with GitHub**

GitHub Projects can be used to create a Kanban board and track tasks alongside the project's source code.

GitHub Issues and commits will support documentation of implementation activities and progress.


## 5. Use of the Gantt Chart

A Gantt chart will be used to prepare and visualize the overall project schedule.

It will represent:

- Major project activities.
- Planned start and completion dates.
- Estimated task durations.
- Dependencies between activities.
- Important project milestones.
- Research, implementation, testing, and documentation periods.

The Gantt chart will provide a high-level overview of the project timeline.

The detailed schedule and the chart itself will be documented separately.

As the project follows Agile, the schedule may be updated when justified by development progress, technical challenges, or research findings.

---


## 6. Project Management Strategy

The project will follow an iterative development strategy.

The main activities will include:

1. Defining project objectives, scope, and requirements.
2. Researching suitable exploration and navigation algorithms.
3. Designing the software architecture.
4. Implementing software components incrementally.
5. Testing components and integrating them with the game host.
6. Evaluating algorithm performance.
7. Improving the implementation based on test results.
8. Documenting the development process and research findings.

Kanban will be used to manage individual tasks, while the Gantt chart will provide an overview of the project timeline.

The developer diary will be maintained to record progress, important decisions, technical problems, and completed activities.

---

## 8. Conclusion

An **Agile software development approach with Kanban task management** has been selected for this project.

Agile provides flexibility for incremental development, experimental algorithm research, and continuous improvement.

Kanban supports individual project management through visual task tracking and flexible prioritization.

The Gantt chart will provide structured time planning and milestone tracking.

Together, these approaches provide a suitable project management structure for developing and evaluating the autonomous Capture the Flag agent.
