# 🛰️ Problem 1 – Investigating the Range as a Function of the Angle of Projection
**Physics** | **Mechanics** | **KW1 Assignment**  
**Author:** Bartu867  
**Date:** March 29, 2025  
---
# 📘 1️⃣ Theoretical Foundation – Projectile Motion

Projectile motion is a classic example of 2D motion under constant acceleration (gravity). It can be broken into two components: **horizontal motion** and **vertical motion**.

---

## ⚙️ Governing Equations from Newton’s Laws

Newton’s Second Law ($F = ma$) applied in the vertical direction gives constant downward acceleration due to gravity.

We ignore air resistance and assume motion starts at ground level.

---

### 🔹 Horizontal Motion (No Acceleration)

- Constant velocity (no force in x-direction)
- Displacement:

  $$x(t) = v_0 \cdot \cos(\theta) \cdot t$$

---

### 🔹 Vertical Motion (Constant Acceleration)

- Acceleration is $-g$ (downward)
- Displacement:

  $$y(t) = v_0 \cdot \sin(\theta) \cdot t - \frac{1}{2}gt^2$$

- Vertical velocity:

  $$v_y(t) = v_0 \cdot \sin(\theta) - gt$$

---

### 🧮 Time of Flight

At landing, $y = 0$:

$$0 = v_0 \cdot \sin(\theta) \cdot t - \frac{1}{2}gt^2$$

Solving for total time $t$:

$$t = \frac{2v_0 \cdot \sin(\theta)}{g}$$

---

### 🎯 Range of the Projectile

Use total flight time in horizontal displacement:

$$R = x(t) = v_0 \cdot \cos(\theta) \cdot t$$

Substitute $t$:

$$R = v_0 \cdot \cos(\theta) \cdot \frac{2v_0 \cdot \sin(\theta)}{g}$$  
$$R = \frac{v_0^2 \cdot \sin(2\theta)}{g}$$

---

## 🔁 Influence of Parameters

- **Initial Velocity ($v_0$):**
    - Range increases quadratically with $v_0$.
    - Doubling $v_0$ results in $4\times$ the range.

- **Gravitational Acceleration ($g$):**
    - Higher $g$ means shorter flight time and range.
    - On the Moon ($g \approx 1.6$), the range is much longer.

- **Angle ($\theta$):**
    - Range is maximum at $\theta = 45^\circ$.
    - $\sin(2\theta)$ creates a symmetric curve around $45^\circ$.

---

## 🧠 Family of Solutions

Changing $v_0$, $g$, or $\theta$ generates a **family of projectile paths** with different ranges and shapes. For example:

- $\theta = 30^\circ$ and $\theta = 60^\circ$ → same range, different height and flight time
- Different $v_0$ values shift the entire trajectory up/down
- Different $g$ values (like Moon vs Earth) stretch the flight arc

---

## 💻 Python Helper Code (Just for Later Use)

```python
import numpy as np
---

# Constants
g = 9.81  # m/s²

# Range function
def range_formula(v0, theta_deg):
    theta_rad = np.radians(theta_deg)
    return (v0 ** 2 * np.sin(2 * theta_rad)) / g
# 📊 2️⃣ Analysis of the Range – Numerical Simulation

In this section, we simulate projectile range behavior with respect to the **launch angle** and analyze how **initial velocity ($v_0$)** and **gravitational acceleration ($g$)** influence the outcome.

---

## 🎯 Objective

- Visualize the function:

  $$R(\theta)=\frac{v_0^2\cdot\sin(2\theta)}{g}$$

- Explore:
  - The symmetry around $\theta=45^\circ$
  - The effect of changing $v_0$ and $g$
  - Optional: Non-zero launch height (extended model)

---

## 💻 Python Code: Range vs Angle (Multiple Cases)

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
theta_deg = np.arange(0, 91, 1)  # angles from 0° to 90°
theta_rad = np.radians(theta_deg)

# Function to calculate range
def range_formula(v0, g, theta):
    return (v0**2 * np.sin(2 * theta)) / g

# Parameters to compare
velocities = [50, 100, 150]  # m/s
gravities = [9.81, 1.62]     # Earth & Moon gravity

# Plot: Range vs Angle for different initial velocities (Earth)
plt.figure(figsize=(10, 5))
for v0 in velocities:
    R = range_formula(v0, 9.81, theta_rad)
    plt.plot(theta_deg, R, label=f"v₀ = {v0} m/s")

plt.title("Range vs Angle for Different Initial Velocities (g = 9.81 m/s²)")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()

# Plot: Range vs Angle on Earth vs Moon
plt.figure(figsize=(10, 5))
for g in gravities:
    R = range_formula(100, g, theta_rad)
    label = "Earth" if g == 9.81 else "Moon"
    plt.plot(theta_deg, R, label=f"{label} (g = {g} m/s²)")

plt.title("Range vs Angle: Earth vs Moon (v₀ = 100 m/s)")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
# 🌍 3️⃣ Practical Applications – Real-World Relevance of Projectile Motion

Projectile motion is more than just a theoretical exercise — it has significant applications in **sports**, **engineering**, and even **space science**. Understanding the factors that affect a projectile's trajectory allows us to model and optimize systems in various domains.

---

## 🏀 Sports

Many sports involve curved projectile trajectories. Understanding these helps in performance analysis, training, and even video game physics engines.

- **Soccer**: Curved free kicks follow projectile paths, especially when lofted.
- **Basketball**: The launch angle of a jump shot determines its chance of scoring.
- **Golf**: Club angle and speed determine the ball’s range and height.

All of these can be modeled using:

$$R=\frac{v_0^2\cdot\sin(2\theta)}{g}$$

But real cases often involve drag and spin.

---

## 🏗️ Engineering

Engineers use projectile models in designing:

- **Military/defense systems** (cannons, missiles, mortars)
- **Fireworks and flare trajectories**
- **Ballistics for forensics and law enforcement**

Precise modeling requires adding:
- Air drag (quadratic with speed)
- Mass of projectile
- Wind vectors

---

## 🚀 Astrophysics & Space Science

In astrophysics, projectile motion generalizes into **orbital mechanics**.

- **Rocket launches** begin with curved trajectories under Earth's gravity
- Escape velocity and reentry modeling depends on projectile motion with air resistance and changing $g$

Also:
- Gravity is not constant:  
  $$g=\frac{GM}{r^2}$$
- Multi-stage motion must be modeled piecewise

---

## 🌄 Uneven Terrain

In real life, projectiles may land:

- On **inclined planes**
- Over **hills, valleys, or obstacles**

This breaks the assumption that the launch and landing height are equal. The range formula becomes invalid, and we must solve:

$$y(t)=h+v_0\cdot\sin(\theta)\cdot t-\frac{1}{2}gt^2$$

using numerical methods to find $t$ when $y(t)=y_{\text{target}}$

---

## 🌬️ External Effects

### 💨 Air Resistance

Air drag opposes motion. It depends on velocity and shape:

$$F_d=\frac{1}{2}C_d\rho Av^2$$

This turns motion into a system of nonlinear differential equations. It shortens range and lowers height.

### 🌪️ Wind

Wind can:
- Increase or decrease horizontal velocity
- Deflect projectile laterally

Simulation must include a horizontal force term.

### 🌕 Variable Gravity

Gravity changes with altitude or location:

- On other planets (e.g., Mars $g=3.71$)
- At high altitudes
- Or due to large terrain differences

Use altitude-based gravity:

$$g(h)=\frac{GM}{(R+h)^2}$$

for accurate modeling in atmospheric reentry or lunar missions.
---
## ✅ Summary

Projectile motion is a versatile model with deep connections to reality. While the idealized equations are helpful, realistic modeling must incorporate:

- Uneven terrain  
- Drag & wind  
- Non-zero launch/landing heights  
- Planet-specific gravity

These improvements enable simulations that match the complexity of real-world systems.
# 💻 4️⃣ Implementation – Simulating Projectile Motion in Python

In this section, we implement a Python-based simulation of projectile motion to analyze how **range** depends on launch angle, initial velocity, gravity, and launch height.

We use the ideal range formula and extend it with optional height-based modeling.

---

## 📌 Ideal Range Formula

The ideal (no air resistance, flat ground) projectile range is given by:

$$R(\theta)=\frac{v_0^2\cdot\sin(2\theta)}{g}$$

Where:
- $R$ is the range (meters)  
- $v_0$ is the initial velocity (m/s)  
- $\theta$ is the launch angle (degrees)  
- $g$ is gravitational acceleration (m/s²)
---
## 💻 Python Code: Basic Implementation

```python
import numpy as np
import matplotlib.pyplot as plt

# Ideal range function
def ideal_range(v0, g, theta_deg):
    theta_rad = np.radians(theta_deg)
    return (v0**2 * np.sin(2 * theta_rad)) / g
angles = np.arange(0, 91, 1)
g = 9.81
velocities = [50, 100, 150]

plt.figure(figsize=(10, 5))
for v0 in velocities:
    ranges = ideal_range(v0, g, angles)
    plt.plot(angles, ranges, label=f"v₀ = {v0} m/s")

plt.title("Projectile Range vs Launch Angle")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
gravities = [9.81, 1.62]  # Earth and Moon gravity
v0 = 100

plt.figure(figsize=(10, 5))
for g_val in gravities:
    ranges = ideal_range(v0, g_val, angles)
    label = "Earth" if g_val == 9.81 else "Moon"
    plt.plot(angles, ranges, label=f"{label} (g = {g_val} m/s²)")

plt.title("Range vs Angle: Earth vs Moon (v₀ = 100 m/s)")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
from scipy.optimize import root_scalar

def range_with_height(v0, g, theta_deg, h):
    theta_rad = np.radians(theta_deg)
    vy0 = v0 * np.sin(theta_rad)
    vx0 = v0 * np.cos(theta_rad)

    def y(t): return h + vy0 * t - 0.5 * g * t**2

    sol = root_scalar(y, bracket=[0.01, 100], method='brentq')
    t_flight = sol.root
    return vx0 * t_flight
heights = [0, 20, 50]
v0 = 100
g = 9.81

plt.figure(figsize=(10, 5))
for h in heights:
    ranges = [range_with_height(v0, g, angle, h) for angle in angles]
    plt.plot(angles, ranges, label=f"Launch Height = {h} m")

plt.title("Projectile Range vs Angle (with Launch Height)")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
