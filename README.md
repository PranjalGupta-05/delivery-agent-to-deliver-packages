# delivery-agent-to-deliver-packages
CSA2001 - Autonomous Delivery Agent Simulator
This project is an interactive, web-based simulator for an autonomous delivery agent navigating a 2D grid city. It's designed to visually demonstrate and compare various pathfinding algorithms, from simple uninformed searches to informed, heuristic-based methods, and even dynamic replanning in response to unexpected obstacles.
This implementation fulfills the requirements for Project 1 of the "Fundamentals of AI and ML" course by providing a hands-on tool for exploring core AI search strategies.
 Features
Interactive Visualization: Watch the agent explore the grid and find the optimal path in real-time.
Multiple Algorithms: Switch between Breadth-First Search (BFS), Uniform-Cost Search (UCS), and A* Search to compare their performance.
Dynamic Replanning: A special "A* with Replanning" mode demonstrates the agent's ability to adapt its path when a sudden obstacle appears.
Varied Environments: Test the algorithms on four distinct maps: a small office, a medium warehouse with terrain costs, a large city block, and a highway with dynamic obstacles.
Performance Metrics: Instantly get key results for each simulation run, including total path cost, number of nodes expanded, and execution time.
Event Log: A detailed log provides a step-by-step commentary of the agent's decision-making process.
Zero Installation: The entire project runs from a single index.html file in any modern web browser. No dependencies or setup required.
 How to Use
Download: Clone this repository or download the delivery_agent_simulator.html file.
Open: Open the delivery_agent_simulator.html file in your preferred web browser (e.g., Chrome, Firefox, Edge).
Simulate:
Use the dropdown menus to select a Map and an Algorithm.
Click the "Start Delivery" button to run the simulation.
Click "Reset" to clear the grid and try a new configuration.
 Environment and Agent Model
Environment: The world is a 2D grid where each cell can be:
Empty: A traversable space.
Wall: A static, impassable obstacle.
Start: The agent's starting position.
End: The package delivery destination.
Terrain Costs: Some maps feature different terrains (Road, Grass, Water) with varying movement costs (Road=1, Grass=3, Water=5), making path selection more complex. This is used by Uniform-Cost Search and A*.
Agent: The agent is rational, aiming to find the most efficient path.
Actions: The agent can move in 4 directions (Up, Down, Left, Right). Diagonal movement is not permitted.
Goal: To find a path from the Start cell to the End cell with the minimum possible cost.
 Algorithms Implemented
The simulator implements three core search strategies as required.
1. Uninformed Search
These algorithms explore the grid without any knowledge of the distance to the goal.
Breadth-First Search (BFS): Explores the grid layer by layer. It guarantees finding the shortest path in terms of the number of steps, but it does not account for terrain costs. It uses a standard FIFO queue.
Uniform-Cost Search (UCS): An evolution of Dijkstra's algorithm. It explores the grid by always expanding the path with the lowest total cost from the start. It guarantees finding the path with the minimum total cost. It uses a priority queue.
2. Informed Search
This algorithm uses a heuristic to estimate the distance to the goal, allowing it to make more intelligent decisions.
A Search:* The premier pathfinding algorithm. It combines the path cost from the start (like UCS) with an estimated cost to the goal. This balance allows it to find the optimal path much more quickly than uninformed methods.
Heuristic Used: Manhattan Distance. This is an admissible heuristic because it calculates the distance on the grid without considering obstacles, meaning it never overestimates the actual cost. h(n) = |current.x - goal.x| + |current.y - goal.y|
3. Local Search / Replanning Strategy
A with Replanning:* This mode simulates a dynamic environment. The agent first calculates an optimal path using A*. It then begins to follow this path, but halfway through, a new Wall obstacle unexpectedly appears on its route. The agent detects this, stops, and re-runs the A* algorithm from its current position to find a new, optimal path to the destination around the new obstacle. This demonstrates a simple but effective replanning strategy.
 Experimental Results & Analysis
(This section is a template for your project report. You should run the simulations and fill this in with your own data and observations.)
Results Table
Map
Algorithm
Path Cost
Nodes Expanded
Time (ms)
Small Office
BFS
XX
XX
XX.XX


UCS
XX
XX
XX.XX


A*
XX
XX
XX.XX
Medium Warehouse
BFS
XX
XX
XX.XX


UCS
XX
XX
XX.XX


A*
XX
XX
XX.XX
Large City Block
BFS
XX
XX
XX.XX


UCS
XX
XX
XX.XX


A*
XX
XX
XX.XX
Replanning
A* (Initial)
XX
XX
XX.XX


A* (Replan)
XX
XX
XX.XX


Total w/ Replan
N/A
XX
XX.XX

Analysis
BFS vs. UCS on Terrain Maps: On maps with varying terrain costs, UCS finds a much cheaper path than BFS because BFS only optimizes for the number of steps, not the cost of those steps.
A Performance:* A* consistently expands the fewest nodes, especially on large, open maps. This is because its heuristic guides it directly toward the goal, avoiding unnecessary exploration in the wrong directions.
Replanning Overhead: The A* with Replanning simulation shows the agent's adaptability. The cost of replanning is the time and computation spent on the second A* search. This demonstrates the trade-off between reacting to dynamic changes and initial planning efficiency.
 
