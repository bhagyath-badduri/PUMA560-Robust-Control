# PUMA 560 Trajectory Tracking using Computed Torque & Robust Min-Max Control

This project presents a **dynamic modeling and control simulation of the PUMA 560 robotic manipulator**, focusing on **trajectory tracking under model uncertainty**.

The system implements both:
- **Computed Torque Control (PD + Inverse Dynamics)**
- **Robust Min-Max Control**

and compares their performance under an **unknown payload disturbance**, highlighting the importance of robustness in real-world robotic systems.

---

## Project Overview

The objective of this project is to analyze trajectory tracking performance of a **6-DOF PUMA 560 robot** under:

- Ideal (nominal) conditions  
- Model uncertainty (unknown payload at end-effector)

The study demonstrates how **model-based controllers degrade under uncertainty**, and how **robust control improves performance**.

---

## Key Features

- Full **dynamic modeling using Lagrangian formulation**
- Implementation of **Computed Torque Control (CTC)**
- Design of **Robust Min-Max controller**
- **Quintic trajectory generation** for smooth motion
- Simulation of **payload uncertainty (2 kg at end-effector)**
- Comparison using:
  - Joint-space tracking error
  - Task-space error
  - RMSE and maximum error

---

## System Modeling

The PUMA 560 dynamics are modeled using:

\[
\tau = M(q)\ddot{q} + C(q,\dot{q})\dot{q} + G(q)
\]

Where:
- \(M(q)\): Inertia matrix  
- \(C(q,\dot{q})\): Coriolis matrix  
- \(G(q)\): Gravity vector  

The model is implemented using **MATLAB Robotics Toolbox** with parameters from Armstrong et al. (1986).

✔ Model validation:
- Compared with **Recursive Newton-Euler (RNE)**
- Error < \(10^{-4}\) Nm (high accuracy)

---

## Controllers Implemented

### 1. Computed Torque Control (CTC)

- Combines:
  - Feedforward inverse dynamics  
  - PD feedback control  

Control law:

\[
\tau = M(q)(\ddot{q}_d + K_d\dot{e} + K_p e) + C(q,\dot{q})\dot{q} + G(q)
\]

✔ Works well under **perfect model conditions**

---

### 2. Robust Min-Max Control

- Designed using:
  - Lyapunov stability principles  
  - Disturbance compensation  

✔ Handles:
- Unknown payload  
- Model mismatch  
- External disturbances  

✔ Improves:
- Tracking accuracy  
- Stability under uncertainty  

---

## Trajectory Generation

A **quintic polynomial trajectory** is used:

- Smooth position, velocity, acceleration
- Zero initial and final velocity & acceleration
- Prevents jerks and vibrations

---

## Simulation Setup

- Robot: PUMA 560 (6-DOF)
- Duration: 5–10 seconds  
- Time step: 0.02 s  
- Controllers tested under:
  - Nominal model  
  - +2 kg payload at end-effector  

---

## Results & Analysis

### Nominal Controller (CTC)

- Excellent tracking under ideal conditions  
- Very low joint error  
- Fast convergence  

### With Payload (Model Uncertainty)

- Significant errors observed, especially:
  - Joint 2 and Joint 3  
- Increased overshoot and oscillations  
- Reduced accuracy in task space  

---

### Robust Min-Max Controller

✔ Key Improvements:

- Reduced joint tracking error across all joints  
- Faster settling time  
- Improved stability  
- Significant reduction in task-space error (especially Z-axis)

---

## Key Observations

- Model-based control (CTC):
  - Works well only with accurate dynamics  
- Payload uncertainty causes:
  - Large tracking errors  
  - Instability in some joints  

- Robust control:
  - Maintains performance despite uncertainty  
  - Essential for real-world robotics  

---

## Visual Results

Include these images in your repo:

- Joint tracking plots (Nominal vs Payload)
- Error plots (Joint + Task space)
- Robot simulation snapshots
- Robust controller comparison plots

---

## Applications

This project is relevant to:

- Industrial robot manipulators  
- Autonomous robotic systems  
- Space robotics  
- Collaborative robots (cobots)  
- Manipulation under uncertainty  

---

## Tools & Technologies

- MATLAB  
- Robotics Toolbox (Peter Corke)  
- Numerical simulation  
- Control systems theory  

---

## Key Concepts Demonstrated

- Robot dynamics (Lagrangian formulation)
- Inverse dynamics control
- PD control tuning
- Robust control design
- Trajectory planning
- Model uncertainty handling

---

## Conclusion

This project demonstrates that:

- **Computed Torque Control performs well only under perfect modeling**
- **Robust Min-Max Control significantly improves tracking under uncertainty**

The results highlight the importance of **robust control strategies in real-world robotic systems**, where exact models are rarely available.

---
