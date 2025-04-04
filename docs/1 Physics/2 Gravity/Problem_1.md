# Problem 1 – Orbital Period and Orbital Radius

**Physics** | **Gravity** | **KW1 Assignment**  
**Author:** Bartu867  
**Date:** March 27, 2025

---

## 🎯 Goal

Understand and derive the relationship between the square of the orbital period and the cube of the orbital radius (Kepler’s Third Law).  
Analyze this for circular orbits and simulate the behavior using Python for different celestial bodies.

---

## 🧠 Theoretical Background

Kepler’s Third Law states that the square of the orbital period \( T \) is proportional to the cube of the orbital radius \( r \) for planets orbiting the same central body:

\[
T^2 \propto r^3
\]

For circular orbits, using Newton’s law of gravitation and centripetal force, the orbital period can be derived as:

\[
T = 2\pi \sqrt{\frac{r^3}{GM}}
\]

Where:  
- \( T \): orbital period (seconds)  
- \( r \): orbital radius (meters)  
- \( G \): gravitational constant \( (6.674 \times 10^{-11} \, \text{Nm}^2/\text{kg}^2) \)  
- \( M \): mass of the central body (kg)

This formula shows that the orbital period increases as the radius increases.

---

## 💻 Python Simulation

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.674e-11  # gravitational constant (m^3/kg/s^2)
M = 5.9722e24  # mass of the Earth (kg)

# Orbital radius values (from 7e6 to 4.2e7 meters)
r = np.linspace(7e6, 4.2e7, 500)

# Orbital period calculation using Kepler's 3rd Law
T = 2 * np.pi * np.sqrt(r**3 / (G * M))  # in seconds

# Plotting
plt.figure(figsize=(10, 6))
plt.plot(r / 1e6, T / 3600, color="orange")  # Convert r to million meters, T to hours
plt.title("Orbital Period vs Orbital Radius")
plt.xlabel("Orbital Radius (Million meters)")
plt.ylabel("Orbital Period (Hours)")
plt.grid(True)
plt.tight_layout()
plt.show()
```

---

