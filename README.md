# BoosterLandingSim 🚀

**BoosterLandingSim** is a physics-based simulator designed to model the vertical landing of a reusable launch vehicle first stage — similar in principle to SpaceX's Falcon 9 booster return.

This project provides a realistic yet modular framework for testing descent profiles, optimizing engine burns, and understanding the physical constraints associated with powered descent and landing in planetary atmospheres.

---

## 🧠 Motivation

With the emergence of reusable rockets, simulating the controlled descent and landing of booster stages has become an important area of research in aerospace engineering and orbital mechanics. This project aims to:

- Understand and model the forces acting on a descending rocket stage
- Explore different landing strategies
- Develop numerical tools for trajectory simulation and optimization
- Serve as a platform for educational or research projects

---

## 🔬 Physics Model

The simulation is based on a 2D vertical motion model (can be extended to 3D later) using Newtonian mechanics and includes the following forces:

### 1. Gravity

The gravitational force is given by:

$$
\vec{F}_g(t) = m(t) \cdot \vec{g} = -m(t) g \vec{e_z}
$$

Where:
- $m$ is the current mass of the booster
- $\vec{g}$ is the gravitational acceleration vector (pointing downwards)

---

### 2. Thrust

Thrust is applied in the direction of the engine nozzle:

$$
\vec{F}_T = T(t) \cdot \vec{u}_{\text{thrust}}
$$

Where:
- $T(t)$ is the time-dependent thrust
- $\vec{u}_{\text{thrust}}$ is the thrust unit vector

---

### 3. Atmospheric Drag

Drag force is modeled using a quadratic drag law:

$$
\vec{F}_D = -\frac{1}{2} \cdot \rho \cdot v^2 \cdot C_D \cdot A \cdot \hat{v}
$$

Where:
- $\rho$ is the atmospheric density
- $v$ is the magnitude of the velocity vector
- $C_D$ is the drag coefficient
- $A$ is the cross-sectional area
- $\hat{v}$ is the unit vector in the direction of velocity

---

## 🧮 Equations of Motion

The system's equations of motion (assuming 1D vertical motion) are:

- Velocity evolution:

$$
\frac{dv}{dt} = \frac{1}{m} \left( T(t) - F_D - m \cdot g \right)
$$

- Position evolution:

$$
\frac{dz}{dt} = v
$$

- Mass loss due to fuel consumption:

$$
\frac{dm}{dt} = -\frac{T(t)}{I_{sp} \cdot g_0}
$$

Where:
- $I_{sp}$ is the specific impulse of the engine
- $g_0$ is the standard gravity

---

## 🧰 Features

- Numerical integration of motion equations (e.g. Runge Kutta 4th order or adaptive step solvers)
- Configurable rocket parameters (mass, thrust profile, drag)
- Atmospheric models (constant or altitude-dependent density)
- Basic control laws for ignition timing and throttle
- Optional visualizations (e.g. Matplotlib plots, animation GIFs)

---

## 📈 Visual Output (Planned)

- Altitude vs. Time
- Velocity vs. Time
- Acceleration, Thrust, and Drag profiles
- Trajectory animation (GIF/MP4)
- Fuel mass vs. time

---

## 🧪 Future Improvements

- 2D/3D simulation with lateral motion
- PID or machine learning-based guidance system
- Optimal control for fuel-efficient landings
- Terrain and landing pad modeling
- Falcon 9 or Starship parameter presets

---

## 🚀 Getting Started

```bash
git clone https://github.com/TristanVrg/BoosterLandingSim.git
cd BoosterLandingSim
pip install -r requirements.txt
python simulator.py
