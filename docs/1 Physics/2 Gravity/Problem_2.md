# 🛰️ Problem 2 – Escape Velocity and Celestial Bodies

**Physics** | **Gravity** | **KW1 Assignment**  
**Author:** Bartu867  
**Date:** March 27, 2025

---

## 🎯 Goal

Examine how escape velocity varies with the mass and radius of a celestial body.  
Understand the concept of escape velocity and simulate how different planetary parameters affect it using Python.

---

## 📘 Theoretical Background

The escape velocity \( v_e \) is the minimum speed required for an object to break free from the gravitational pull of a massive body, without any further propulsion.

The formula is derived from energy conservation:  
\[
v_e = \sqrt{\frac{2GM}{R}}
\]

Where:
- \( v_e \): escape velocity (m/s)
- \( G \): gravitational constant \( 6.674 \times 10^{-11} \, \text{Nm}^2/\text{kg}^2 \)
- \( M \): mass of the celestial body (kg)
- \( R \): radius of the celestial body (m)

---

## 💻 Python Simulation

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.674e-11  # Gravitational constant

# Example celestial body masses (kg) and radii (m)
masses = np.array([5.972e24, 6.39e23, 1.898e27])  # Earth, Mars, Jupiter
radii = np.array([6.371e6, 3.3895e6, 6.9911e7])   # Earth, Mars, Jupiter
names = ['Earth', 'Mars', 'Jupiter']

# Escape velocity calculation
v_escape = np.sqrt(2 * G * masses / radii)

# Plotting
plt.figure(figsize=(10,6))
plt.bar(names, v_escape, color='crimson')
plt.title("Escape Velocity for Different Celestial Bodies")
plt.ylabel("Escape Velocity (m/s)")
plt.grid(axis='y')
plt.tight_layout()
plt.show()
