# Monte Carlo Robot Path Finding

This project implements a reinforcement learning approach for grid-based robot path finding using First-Visit Monte Carlo Control.

The objective is to train an agent to navigate from a starting position to a target location while avoiding obstacles and respecting velocity constraints. The agent learns an effective navigation policy through interaction with the environment and episode-based learning.

## Project Overview

The environment consists of a two-dimensional grid containing:

* Starting positions
* Target location
* Obstacles
* Empty cells

The agent moves using velocity-based dynamics. At each step, it can adjust its velocity and move across the grid accordingly. Collisions with obstacles or boundaries reset the agent to a valid starting position.

The learning algorithm is based on First-Visit Monte Carlo Control with ε-greedy policy improvement.

## Environment

### State Representation

Each state is represented as:

```text
(row, col, vx, vy)
```

where:

* `row`, `col` represent the current position
* `vx`, `vy` represent the current velocity

### Action Space

The agent selects velocity increments:

```text
Δvx ∈ {-1, 0, 1}
Δvy ∈ {-1, 0, 1}
```

resulting in 9 possible actions.

### Reward Function

* Reward = -1 for each time step
* Episode terminates when the target is reached

This encourages the agent to find the shortest path to the goal.

## Reinforcement Learning Method

The project uses First-Visit Monte Carlo Control.

### Algorithm

1. Initialize state-action values Q(s,a)
2. Generate episodes using an ε-greedy policy
3. Compute returns for each state-action pair
4. Update Q-values using average observed returns
5. Improve the policy by selecting actions with the highest estimated value
6. Gradually reduce ε during training

### Parameters

* Discount factor (γ): 0.9
* ε-greedy exploration
* First-Visit Monte Carlo updates

## Project Structure

```text
Monte Carlo Control Path Finding/
│
├── environment.py
├── grids.py
├── main.py
├── mc_control.py
├── visualization.py
├── README.md
│
└── plots/
    ├── experiment_summary.csv
    ├── Grid-1_path.png
    ├── Grid-2_path.png
    ├── Grid-3_path.png
    └── Grid-4_path.png
```

## Results

The algorithm was evaluated on multiple grid configurations with different obstacle layouts.

Key observations:

* The agent successfully learns paths to the target.
* Training time depends on environment complexity.
* Obstacle count alone does not determine runtime.
* More restrictive layouts can sometimes reduce exploration time.
* Monte Carlo Control learns effective navigation policies without requiring an environment model.

Example visualizations are available in the `plots` directory.

## Technologies

* Python
* NumPy
* Matplotlib
* Reinforcement Learning
* Monte Carlo Control

## Team

This project was completed as part of a university Reinforcement Learning assignment.

Team Members:

* Sohel Rana
* Almat Akhatov
* Md Abdul Kayum

## License

This repository is provided for educational and portfolio purposes.
