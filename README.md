# 🚀 BoosterLandingSim

**BoosterLandingSim** is an open-source physics-based simulator for the vertical landing of a reusable rocket booster, inspired by vehicles like SpaceX’s Falcon 9.  
It models the atmospheric descent phase using realistic physics: gravity, drag, and engine thrust — with the goal of building an educational, scientific, and engineering-grade simulation.

---

## 🧠 Project Goals

- Understand the dynamics of controlled booster descent.
- Build a realistic numerical simulator from first principles.
- Implement and test control algorithms (PID, optimal control, etc.).
- Provide a sandbox for visualization, prototyping, and optimization.

---

## 📐 Physics Model

This simulator models a **rigid body in vertical descent**, subject to the following forces:

### 🔺 Forces included

1. **Gravity**  
   \[
   F_g = m \cdot g
   \]  
   where \( m \) is the instantaneous mass, and \( g = 9.81\, \mathrm{m/s^2} \).

2. **Engine Thrust (vectorized)**  
   \[
   \vec{F}_T = T(t) \cdot \hat{u}_{thrust}
   \]  
   with \( T(t) \) the thrust as a function of time, and \( \hat{u}_{thrust} \) the thrust direction.

3. **Aerodynamic Drag**  
   \[
   \vec{F}_D = -\frac{1}{2} \cdot \rho \cdot v^2 \cdot C_D \cdot A \cdot \hat{v}
   \]  
   where \( \rho \) is air density, \( C_D \) the drag coefficient, \( A \) the frontal area, and \( \hat{v} \) the velocity unit vector.

4. **Control Torque (optional)**  
   To simulate grid fins or gimbaled thrust in a 2D/3D extension.

---

## 🧮 Equations of Motion

For a basic 1D vertical case:
\[
\frac{dv}{dt} = \frac{1}{m} \left( T(t) - F_D - m \cdot g \right)
\]
\[
\frac{dz}{dt} = v
\]

With fuel consumption:
\[
\frac{dm}{dt} = -\frac{T(t)}{I_{sp} \cdot g_0}
\]

Extensions to 2D or 3D can include angular dynamics and full vector control.

---

## 🧰 Tech Stack

- **Python 3.10+**
- `numpy`, `scipy` for numerical integration and physics
- `matplotlib` for trajectory visualization
- (Optional) `pygame` or `manim` for animations
- (Planned) `PyTorch` / `TensorFlow` for control learning

---

## 🎯 Features & Roadmap

| Feature                          | Status      |
|----------------------------------|-------------|
| 1D gravity + thrust dynamics     | ✅ Done      |
| Atmospheric drag                 | ✅ Done      |
| Manual thrust profile            | ✅ In Progress |
| PID control                      | 🟡 Planned   |
| Trajectory visualization         | ✅ Complete  |
| 2D dynamics with gimbaled thrust | 🔲 Coming    |
| Thrust profile optimization      | 🔲 Planned   |
| Reinforcement learning control   | 🔲 Idea stage|

---

## 📸 Preview

![demo](assets/demo.gif)

> Animation: vertical descent with final retropropulsive braking.

---

## 📦 Installation

```bash
git clone https://github.com/your-username/BoosterLandingSim.git
cd BoosterLandingSim
pip install -r requirements.txt
python simulator.py
