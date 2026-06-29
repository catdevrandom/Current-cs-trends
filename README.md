# CS 370 – Pirate Intelligent Agent
### Deep Q-Learning | Keras & TensorFlow | Juan Pablo Gil

---

## Project Overview

This project implements a **deep Q-learning (DQN)** algorithm to train a pirate intelligent agent to navigate an 8×8 treasure hunt maze. The agent learns to find the optimal path to the treasure by maximizing cumulative reward through trial, error, and experience replay.

---

## What Was Given vs. What I Built

### Provided (Starter Code)
| File / Function | Description |
|---|---|
| `TreasureMaze.py` | Maze environment — handles state, movement, and rewards |
| `GameExperience.py` | Experience replay memory and batch data retrieval |
| `build_model()` | Keras Sequential neural network with PReLU activations |
| `train_step()` | TensorFlow GradientTape training step |
| `play_game()` | Simulates a full game using a trained model |
| `completion_check()` | Validates the agent wins from every starting position |
| `show()` | Visualizes the maze state using matplotlib |

### My Contribution — `qtrain()` Function
I implemented the complete training loop, including:

- **Epoch loop** with random starting cell selection each episode
- **Epsilon-greedy action selection** — balances exploration (random valid moves) vs. exploitation (model predictions)
- **Episode storage** using `experience.remember()`
- **Batch training** via `experience.get_data()` and `train_step()`
- **Target network** that syncs every 50 epochs to stabilize Q-value updates
- **Dynamic epsilon adjustment** — collapses to 0.05 when win rate exceeds 90%
- **Early stopping** — halts training when win rate ≥ 99.9% and `completion_check()` confirms the agent solves the maze from all starting positions

---

## Key Concepts Applied

- **Reinforcement Learning** — agent learns via reward signals, not labeled data
- **Deep Q-Network (DQN)** — neural network approximates Q-values for each action
- **Bellman Equation** — used to compute target Q-values during training
- **Experience Replay** — random sampling from memory breaks correlation between sequential steps
- **Epsilon-Greedy Strategy** — exploration decays over time as the agent learns

---

## Reflection

### What do computer scientists do and why does it matter?
Computer scientists design systems that solve real problems — from routing traffic to diagnosing disease to training intelligent agents. What makes this work meaningful is that these systems increasingly make or inform decisions that affect people's lives. In this project, the problem was a maze game, but the underlying techniques — reinforcement learning, neural networks, reward optimization — are the same ones powering autonomous vehicles, robotics, and medical diagnostics. Computer scientists matter because they translate complex, messy real-world problems into systems that can learn, adapt, and scale.

### How do I approach a problem as a computer scientist?
I break problems into smaller, testable components. In this project, that meant understanding the environment and state space first, then building the training loop piece by piece — getting exploration working before adding exploitation, then layering in experience replay, then the target network. When the agent failed to converge, I treated it as a debugging problem: adjusting epsilon decay, batch size, and target update frequency systematically rather than randomly. This course reinforced that good computer scientists don't just write code — they form hypotheses, test them, and iterate based on evidence.

### What are my ethical responsibilities to the end user and the organization?
AI systems carry real ethical weight. As a developer, my responsibility is to ensure a system behaves reliably, transparently, and fairly. In this project, that means understanding *why* the agent makes certain routing decisions, not just whether it wins. In production systems, this translates to avoiding black-box models where accountability is unclear, protecting user data involved in training, and being honest about a model's limitations. The `completion_check()` function is itself an example of responsible design — it verifies the agent generalizes across all starting positions rather than just performing well on average. Organizations deploying AI must prioritize safety and fairness over efficiency, and computer scientists are the ones who build those safeguards in from the start.

---

## Technologies Used
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=flat&logo=keras&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)

---

*Southern New Hampshire University — CS 370: Current/Emerging Trends in Computer Science*
