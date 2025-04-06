# 🔬 Physics Assignment – KW1  
**Topic:** Mechanics – Oscillations & Motion  
**Author:** Bartu867  
**Date:** March 27, 2025  

---

# Problem 1 – Investigating the Dynamics of a Forced Damped Pendulum

## 🎯 Goal

Analyze the motion of a forced damped pendulum and observe how different parameters influence its behavior — including regular, resonant, and chaotic motion.

---

## 📘 Theoretical Background

The motion of a forced damped pendulum is governed by the second-order nonlinear differential equation:

d²θ/dt² + b(dθ/dt) + ω₀² sin(θ) = A cos(ωt)

Where:
- θ: angular displacement  
- b: damping coefficient  
- ω₀: natural frequency  
- A: amplitude of external force  
- ω: driving frequency  

---

## 🔢 Reformulated System (First-Order)

To apply numerical methods, the second-order ODE is transformed into two coupled first-order ODEs:

Let ω = dθ/dt, then:

dθ/dt = ω  
dω/dt = -bω - ω₀² sin(θ) + A cos(ωt)

---

## 🧠 Numerical Method: Runge-Kutta 4th Order (RK4)

The RK4 method is used to solve the equations. The update steps for each time interval dt:

θₙ₊₁ = θₙ + (1/6)(k1_θ + 2k2_θ + 2k3_θ + k4_θ)  
ωₙ₊₁ = ωₙ + (1/6)(k1_ω + 2k2_ω + 2k3_ω + k4_ω)

---

## 💻 Python Code – Pendulum Simulation

```python
import numpy as np
import matplotlib.pyplot as plt

# Parameters
b = 0.5              # damping coefficient
w0 = 1.5             # natural frequency
A = 1.2              # driving force amplitude
w = 0.666            # driving frequency
dt = 0.04            # time step
T = 100              # total simulation time

# Time array
t = np.arange(0, T, dt)

# Arrays for theta and omega
theta = np.zeros_like(t)
omega = np.zeros_like(t)

# Initial conditions
theta[0] = 0.2
omega[0] = 0.0

# Runge-Kutta 4th order method
for i in range(1, len(t)):
    k1_theta = dt * omega[i - 1]
    k1_omega = dt * (-b * omega[i - 1] - w0**2 * np.sin(theta[i - 1]) + A * np.cos(w * t[i - 1]))

    k2_theta = dt * (omega[i - 1] + 0.5 * k1_omega)
    k2_omega = dt * (-b * (omega[i - 1] + 0.5 * k1_omega) - w0**2 * np.sin(theta[i - 1] + 0.5 * k1_theta) + A * np.cos(w * (t[i - 1] + 0.5 * dt)))

    k3_theta = dt * (omega[i - 1] + 0.5 * k2_omega)
    k3_omega = dt * (-b * (omega[i - 1] + 0.5 * k2_omega) - w0**2 * np.sin(theta[i - 1] + 0.5 * k2_theta) + A * np.cos(w * (t[i - 1] + 0.5 * dt)))

    k4_theta = dt * (omega[i - 1] + k3_omega)
    k4_omega = dt * (-b * (omega[i - 1] + k3_omega) - w0**2 * np.sin(theta[i - 1] + k3_theta) + A * np.cos(w * (t[i - 1] + dt)))

    theta[i] = theta[i - 1] + (k1_theta + 2 * k2_theta + 2 * k3_theta + k4_theta) / 6
    omega[i] = omega[i - 1] + (k1_omega + 2 * k2_omega + 2 * k3_omega + k4_omega) / 6

# Plotting
plt.figure(figsize=(10, 5))
plt.plot(t, theta)
plt.title("Forced Damped Pendulum – Angular Displacement Over Time")
plt.xlabel("Time (s)")
plt.ylabel("Angle (rad)")
plt.grid(True)
plt.show()
