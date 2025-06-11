Here's a detailed and polished `README.md` for your NEAT Car Simulation project:

---

# 🧠 NEAT Self-Driving Car Simulation

This project simulates autonomous car driving using the **NEAT (NeuroEvolution of Augmenting Topologies)** algorithm. The AI agents (cars) learn how to navigate a map through evolution — no supervised learning, no backpropagation — just raw neuroevolution.

Built using **Python**, **Pygame**, and **NEAT-Python**, this project demonstrates how evolutionary neural networks can be applied to solve complex control problems like navigation and obstacle avoidance.

---

## 🚗 Features

* Evolving neural networks using NEAT
* Physics-inspired car dynamics and collision detection
* Simulated radar sensor inputs (like LIDAR)
* Trail tracking for visual debugging
* Custom assets (car and map images)
* Real-time visualization with Pygame

---

## 🗂️ Project Structure

```
NeatCarSimulation/
├── core/
│   ├── assets/
│   │   ├── car.png           # Car sprite
│   │   └── map2.png          # Track/map image
│   ├── config.py             # Simulation constants
│   ├── car.py                # Car dynamics, sensors, rewards
│   ├── utils.py              # Collision detection
│   └── simulation.py         # NEAT integration and simulation logic
├── main.py                   # Program entry point
└── core/config-feedforward.txt  # NEAT configuration file
```

---

## ⚙️ Requirements

Install the dependencies with:

```bash
pip install pygame neat-python
```

---

## ▶️ How to Run

Simply launch:

```bash
python main.py
```

The simulation will evolve 100 generations of cars trying to complete the track.

---

## 🧬 NEAT Setup

The configuration for the NEAT algorithm is defined in `Assets/config.txt`. This includes:

* Input and output sizes
* Mutation rates
* Compatibility thresholds
* Activation functions
* Population size, etc.

The network inputs are simulated radar distances at various angles. The output is a single float (0 to 1) controlling the steering angle.

---

## 🧠 Inputs to the Neural Network

Each car has multiple virtual radars (7 by default), which serve as the input to the neural network. These radars simulate distance to the nearest wall in a specific direction:

```python
RADAR_ANGLES = [-90, -60, -30, 0, 30, 60, 90]
```

These are then fed into the NEAT-generated neural network to decide how to steer.

---

## 🏁 Fitness Function

Cars are rewarded based on:

* **Radar distance**: higher values mean the car is far from obstacles.
* **Survival time**: the longer a car stays alive, the more it can learn.

```python
genome.fitness += car.get_reward()
```

This encourages agents to explore while avoiding collisions.

---

## 🧹 Future Improvements

* Add checkpoints or laps as explicit goals
* Enable reverse movement and acceleration control
* Allow evolution of more complex behaviors (e.g., overtaking)
* Add multiple tracks and procedurally generate maps
* Export trained networks and replay them

---


## 📄 License

This project is licensed under the **MIT License** — feel free to use, modify, and share.

