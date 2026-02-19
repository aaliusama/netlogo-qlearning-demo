# NetLogo Reinforcement Learning: Q-Learning Path Finding

A demonstration of reinforcement learning using Q-learning algorithm implemented in NetLogo. An agent learns to navigate from a start position to a goal while avoiding obstacles through trial and error.

![NetLogo RL Demo](https://img.shields.io/badge/NetLogo-6.x-blue.svg)

## Overview

This project demonstrates how an autonomous agent can learn optimal navigation strategies using Q-learning, a model-free reinforcement learning algorithm. The agent explores a grid environment, learning from rewards and penalties to find the shortest path from start to goal.

## What is Q-Learning?

Q-learning is a value-based reinforcement learning algorithm that learns the quality (Q-value) of actions in different states. The agent:
- **Explores** the environment through random actions
- **Exploits** learned knowledge to take optimal actions
- **Updates** Q-values based on rewards received
- **Converges** to an optimal policy over time

### Key Concepts

- **State**: Current position of the agent in the grid
- **Action**: Move up, down, left, or right
- **Reward**: Feedback from environment (+5 for goal, -0.04 per step, -1 for walls)
- **Q-value**: Expected future reward for taking an action in a state
- **Policy**: Strategy the agent follows (epsilon-greedy)

## Features

- **Visual Learning Process**: Watch the agent explore and learn in real-time
- **Adjustable Hyperparameters**: Tune learning rate, discount factor, and exploration rate
- **Performance Tracking**: Monitor episode rewards and path lengths
- **Learned Path Visualization**: Display the optimal path after training
- **Random Obstacle Generation**: Different layouts for each run

## Requirements

- **NetLogo 6.x** or higher
- Download from: [https://ccl.northwestern.edu/netlogo/](https://ccl.northwestern.edu/netlogo/)

## How to Use

### 1. Setup

1. Open `q-learning-pathfinding.nlogo` in NetLogo
2. Adjust hyperparameters using sliders:
   - **alpha** (learning rate): How quickly the agent learns (0.1 - 0.5 recommended)
   - **gamma** (discount factor): Importance of future rewards (0.8 - 0.95 recommended)
   - **epsilon** (exploration rate): Balance between exploration and exploitation (0.1 - 0.3 recommended)
   - **step-penalty**: Cost per step (-0.01 to -0.1)
   - **goal-reward**: Reward for reaching goal (5 - 10)

3. Click **Setup** to initialize the environment

### 2. Training

1. Click **Go** to start training
2. Observe:
   - Red turtle exploring the environment
   - Pen trail showing visited paths
   - Patches changing color (yellow intensity = learned value)
   - Plots updating with performance metrics

3. Let it run for **1000-5000 ticks** for good convergence

### 3. Visualize Results

1. Click **Show Learned Path** to see the optimal route
2. Yellow turtle will demonstrate the learned shortest path
3. Monitor displays:
   - **Episodes**: Number of training episodes completed
   - **Best Path**: Shortest path length found
   - **Q-values**: Current Q-values of the agent

##  Understanding the Results

### Episode Reward Plot
- Shows cumulative reward per episode
- Should increase over time as agent learns
- Negative initially (many steps), positive later (efficient paths)

### Steps per Episode Plot
- Shows path length for each episode
- Should decrease as agent finds shorter routes
- Convergence indicates successful learning

### Color Visualization
- **Blue**: Start position
- **Green**: Goal position
- **Black**: Obstacles/walls
- **Yellow gradient**: Learned state values (brighter = higher value)
- **Red**: Learning agent
- **Yellow turtle**: Demonstrating learned policy

## Hyperparameter Tuning Guide

| Parameter | Low Value | High Value | Effect |
|-----------|-----------|------------|--------|
| **alpha** (0.2) | Slow, stable learning | Fast, unstable learning | Learning speed |
| **gamma** (0.9) | Short-sighted (immediate rewards) | Far-sighted (future rewards) | Planning horizon |
| **epsilon** (0.2) | More exploitation | More exploration | Exploration vs exploitation |

### Recommended Settings

**Fast Learning:**
- alpha = 0.3
- gamma = 0.9
- epsilon = 0.3

**Stable Learning:**
- alpha = 0.1
- gamma = 0.95
- epsilon = 0.1

**Balanced:**
- alpha = 0.2
- gamma = 0.9
- epsilon = 0.2

## 🎓 Educational Use

This model is perfect for:
- Teaching reinforcement learning concepts
- Demonstrating agent-based modeling
- Understanding exploration-exploitation tradeoff
- Visualizing learning dynamics
- Comparing different hyperparameter settings

## Algorithm Details

### Q-Learning Update Rule

```
Q(s,a) ← Q(s,a) + α[r + γ·max(Q(s',a')) - Q(s,a)]
```

Where:
- `Q(s,a)`: Q-value for state s and action a
- `α`: Learning rate
- `r`: Immediate reward
- `γ`: Discount factor
- `max(Q(s',a'))`: Maximum Q-value in next state

### Epsilon-Greedy Policy

```
action = {
  random action,           with probability ε (explore)
  argmax Q(s,a),          with probability 1-ε (exploit)
}
```

## 🛠️ Code Structure

```
q-learning-pathfinding.nlogo
│
├── Globals
│   ├── learn-rate (alpha)
│   ├── discount (gamma)
│   ├── explore-rate (epsilon)
│   └── episode-reward
│
├── Agent Properties (turtles-own)
│   ├── q [up, down, left, right]
│   └── steps-this-episode
│
├── Environment (patches-own)
│   ├── reward
│   └── visit-count
│
├── Procedures
│   ├── setup: Initialize environment
│   ├── go: Main training loop
│   └── show-learned-path: Visualize learned policy
```

##  Experiments to Try

1. **Effect of Learning Rate**: Try alpha = 0.1, 0.5, 0.9
2. **Exploration vs Exploitation**: Compare epsilon = 0.1 vs 0.5
3. **Obstacle Density**: Modify number of walls (line 52)
4. **Reward Shaping**: Adjust step-penalty and goal-reward
5. **Grid Size**: Change world dimensions in settings

## Troubleshooting

**Agent gets stuck:**
- Increase exploration rate (epsilon)
- Reduce obstacle density
- Increase timeout threshold (line 121)

**Learning is too slow:**
- Increase learning rate (alpha)
- Increase goal reward
- Reduce step penalty

**Agent doesn't converge:**
- Decrease learning rate for stability
- Increase discount factor
- Run for more episodes

## Further Reading

- [Sutton & Barto - Reinforcement Learning: An Introduction](http://incompleteideas.net/book/the-book.html)
- [Q-Learning Explained](https://en.wikipedia.org/wiki/Q-learning)
- [NetLogo Documentation](https://ccl.northwestern.edu/netlogo/docs/)




**Keywords**: Reinforcement Learning, Q-Learning, Agent-Based Modeling, NetLogo, Path Finding, Artificial Intelligence, Machine Learning, Educational AI
