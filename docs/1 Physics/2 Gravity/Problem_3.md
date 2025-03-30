# 🛰️ Problem 3 – Trajectories of a Freely Released Payload Near Earth

**Physics** | **Gravity** | **KW1 Assignment**  
**Author:** Bartu867  
**Date:** March 29, 2025

---

## 🎯 Goal

Simulate and analyze the possible trajectories of a payload released near Earth from a moving spacecraft.  
Determine whether the object enters orbit, falls to Earth, or escapes into space depending on initial conditions.

---

## 📘 Theoretical Background

When an object is released from a spacecraft near Earth, it will follow a trajectory determined by its initial velocity and position relative to Earth's gravity.

Using Newton's law of universal gravitation:

\[
F = \frac{GMm}{r^2}
\]

The motion of the payload follows Newton's second law:

\[
F = ma \Rightarrow a = \frac{GM}{r^2}
\]

Depending on the initial velocity vector:

- If \( v < v_{\text{orbit}} \), it falls back to Earth.
- If \( v = v_{\text{orbit}} \), it enters circular orbit.
- If \( v > v_{\text{escape}} \), it escapes Earth's gravity.

We will simulate the trajectory by numerically integrating the motion under gravitational acceleration.

---

## 💻 Python Simulation

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.674e-11              # gravitational constant (m^3/kg/s^2)
M = 5.972e24               # mass of Earth (kg)
R = 6.371e6                # radius of Earth (m)

# Initial conditions
r0 = np.array([7.0e6, 0])                      # initial position (just above Earth surface)
v0 = np.array([0, 8000])                       # initial velocity in m/s (tangential)

# Simulation parameters
dt = 1                                          # time step (seconds)
steps = 10000                                   # number of steps

# Arrays to store trajectory
positions = np.zeros((steps, 2))
velocities = np.zeros((steps, 2))

# Set initial values
positions[0] = r0
velocities[0] = v0

# Simulation loop
for i in range(1, steps):
    r = positions[i-1]
    v = velocities[i-1]
    dist = np.linalg.norm(r)
    
    if dist < R:
        positions = positions[:i]  # Break if the object is within Earth's radius
        break
    
    # Gravitational acceleration
    a = -G * M * r / dist**3
    
    # Update velocity and position (Euler method)
    velocities[i] = v + a * dt
    positions[i] = r + velocities[i] * dt

# Plotting the trajectory
x = positions[:, 0] / 1000  # Convert to km
y = positions[:, 1] / 1000  # Convert to km

plt.figure(figsize=(8,8))
plt.plot(x, y, label='Payload trajectory')
circle = plt.Circle((0, 0), R / 1000, color='blue', alpha=0.5, label='Earth')
plt.gca().add_patch(circle)
plt.xlabel("x position (km)")
plt.ylabel("y position (km)")
plt.title("Trajectory of Payload Released Near Earth")
plt.axis("equal")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
