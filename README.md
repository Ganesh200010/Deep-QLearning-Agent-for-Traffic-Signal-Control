# 🚦 Deep Q-Learning Agent for Traffic Signal Control

This project implements an intelligent traffic signal control system using **Deep Q-Learning** and the **SUMO traffic simulator**. The goal is to reduce traffic congestion and waiting time at intersections by training an agent that dynamically adapts traffic light phases based on real-time traffic conditions.

---

## 🧠 Project Overview

Traditional traffic lights operate on fixed schedules, causing inefficiencies during fluctuating traffic. Our agent learns to optimize light switching policies by minimizing cumulative vehicle delay and queue lengths at a four-way intersection using reinforcement learning.

---

## 🔍 Key Features

- Deep Q-Learning using TensorFlow/Keras
- Traffic simulation with SUMO
- Custom reward function based on vehicle waiting time
- Vehicle generation using Weibull distribution
- Epsilon-greedy policy for exploration-exploitation
- Visualization of training and test results

---

## 🛠️ Project Components

### 1. `training_main.py`
Initializes the agent and runs training episodes, recording:
- Cumulative reward
- Queue length
- Delay  

### 2. `training_simulation.py`
Simulates each episode, gathers state info, applies actions, collects rewards, and trains the model using replay memory.  

### 3. `model.py`
Defines the architecture of a fully connected deep Q-network, supports training and inference.  

### 4. `memory.py`
Stores past experiences and samples them randomly to train the agent.  

### 5. `generator.py`
Generates realistic vehicle routes and traffic patterns using Weibull distribution.  

### 6. `visualization.py`
Creates and saves plots of performance metrics like reward, delay, and queue length.  

### 7. `utils.py`
Handles configuration parsing, SUMO setup, and directory management.  

### 8. `testing_main.py` & `testing_simulation.py`
Loads a trained model and runs a test simulation, outputting plots without training.  

---

## ⚙️ Configuration Files

- `training_settings.ini`: Defines training parameters like episodes, batch size, model layers, and learning rate.  

- `testing_settings.ini`: Defines test parameters including GUI setting, max steps, and model index to test.  

---

## 📈 State Representation

The state is represented as an array of 80 binary cells indicating vehicle positions at different lanes and distances from the traffic light.  

---

## 🧮 Action Space

The agent can choose between 4 actions, each representing a traffic light phase:
1. NS Green
2. NSL Green
3. EW Green
4. EWL Green  

---

## 🧪 Reward System

Reward is calculated as the negative change in total vehicle waiting time. The agent learns to minimize waiting time and queue length across episodes.  

---

## 📊 Output

- Plots of:
  - Cumulative reward vs episodes
  - Queue length vs steps
  - Delay vs episodes
- Trained models saved as `.h5` and visualized with `.png` diagrams.  

---

## 🚧 Requirements

- Python 3.6+
- TensorFlow/Keras
- SUMO Simulator
- `SUMO_HOME` environment variable set

---

## ▶️ How to Run

### 🏁 Train the Agent

```bash
python training_main.py
