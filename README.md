# Taxi-v3 Reinforcement Learning with Q-Learning 🚕

This project implements a **Q-Learning** agent to solve the OpenAI Gym (Gymnasium) **Taxi-v3** environment. The agent learns an optimal policy to pick up a passenger at one of four locations and drop them off at a specific destination in the fewest steps possible.



## 📋 Table of Contents
* [Overview](#overview)
* [The Environment](#the-environment)
* [The Algorithm](#the-algorithm)
* [Hyperparameters](#hyperparameters)
* [Installation](#installation)
* [Usage](#usage)

---

## 🔍 Overview
The Taxi problem is a classic Reinforcement Learning task. The goal is to move a taxi on a $5 \times 5$ grid, navigate around walls, pick up a passenger, and drop them off at the correct destination. 

## 🌍 The Environment
* **State Space:** 500 discrete states (based on Taxi coordinates, passenger location, and destination).
* **Action Space:** 6 discrete actions:
  - `0`: Move South
  - `1`: Move North
  - `2`: Move East
  - `3`: Move West
  - `4`: Pickup passenger
  - `5`: Drop off passenger
* **Rewards:** - `-1` for each step (encourages speed).
  - `+20` for successful drop-off.
  - `-10` for illegal pickup/drop-off.

---

## 🧠 The Algorithm
This project uses **Q-Learning**, an off-policy reinforcement learning algorithm. It builds a **Q-Table** where each cell represents the "quality" of an action in a given state.

The Q-values are updated using the Bellman equation:
$$Q(s, a) \leftarrow (1 - \alpha) Q(s, a) + \alpha \left( r + \gamma \max_{a'} Q(s', a') \right)$$



### Exploration vs. Exploitation
We use an **$\epsilon$-Greedy Strategy**:
1. **Exploration:** The agent takes random actions to discover the environment.
2. **Exploitation:** The agent uses the Q-table to take the best-known action.
The exploration rate ($\epsilon$) decays over time, allowing the agent to settle into its learned strategy.

---

## ⚙️ Hyperparameters

| Parameter | Value | Description |
| :--- | :--- | :--- |
| **Learning Rate ($\alpha$)** | 0.9 | How much new information overrides old information. |
| **Discount Factor ($\gamma$)** | 0.95 | Importance of future rewards vs. immediate rewards. |
| **Initial Epsilon ($\epsilon$)** | 1.0 | Starting exploration probability. |
| **Epsilon Decay** | 0.9995 | Multiplier to reduce $\epsilon$ after each episode. |
| **Min Epsilon** | 0.01 | Minimum threshold for exploration. |
| **Episodes** | 10,000 | Total training iterations. |

---

## 🛠️ Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/cosmicbit/qlearningtaxigame.git
   cd qlearningtaxigame
   ```

2. **Ensure you have Python installed, then install the required dependencies:**
   ```bash
   pip install gymnasium numpy
   ```

## 🚀 Usage

1. **Training:** Run the script to start the training process.
   ```bash
   python main.py
   ```
   
2. **Testing:** Once the 10,000 episodes are complete, the script will automatically switch to "human" render mode. A graphical window will open, and you can watch the trained taxi agent complete 5 test episodes efficiently.
