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
# 📊 2️⃣ Analysis of the Range – Numerical Investigation

We now numerically investigate how the **range of a projectile** depends on various parameters:

- Launch angle $\theta$
- Initial velocity $v_0$
- Gravitational acceleration $g$
- Launch height $h$ (optional)

---

## 🎯 Governing Equation (Ideal Case)

The ideal range equation (no air resistance, flat terrain):

$$R(\theta)=\frac{v_0^2\cdot\sin(2\theta)}{g}$$

- $R$: horizontal range (meters)  
- $v_0$: initial speed  
- $\theta$: launch angle  
- $g$: gravitational acceleration

---

## 💻 Python Code: Range vs Launch Angle
![alt text](image-1.png)
```python
import numpy as np
import matplotlib.pyplot as plt

def ideal_range(v0, g, theta_deg):
    theta_rad = np.radians(theta_deg)
    return (v0**2 * np.sin(2 * theta_rad)) / g

# Angle values
angles = np.arange(0, 91, 1)  # 0° to 90°

# Plot for different initial velocities
g = 9.81  # Earth gravity
velocities = [50, 100, 150]

plt.figure(figsize=(10, 5))
for v0 in velocities:
    ranges = ideal_range(v0, g, angles)
    plt.plot(angles, ranges, label=f"v₀ = {v0} m/s")

plt.title("Range vs Launch Angle – Different Initial Velocities")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
gravities = [9.81, 1.62]  # Earth and Moon
v0 = 100

plt.figure(figsize=(10, 5))
for g_val in gravities:
    ranges = ideal_range(v0, g_val, angles)
    label = "Earth" if g_val == 9.81 else "Moon"
    plt.plot(angles, ranges, label=f"{label} (g = {g_val} m/s²)")

plt.title("Range vs Angle on Earth and Moon")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
from scipy.optimize import root_scalar

def range_with_height(v0, g, theta_deg, h):
    theta_rad = np.radians(theta_deg)
    vy = v0 * np.sin(theta_rad)
    vx = v0 * np.cos(theta_rad)

    def y(t): return h + vy * t - 0.5 * g * t**2

    sol = root_scalar(y, bracket=[0.01, 100], method='brentq')
    t_flight = sol.root
    return vx * t_flight

# Compare different launch heights
heights = [0, 20, 50]
v0 = 100
g = 9.81

plt.figure(figsize=(10, 5))
for h in heights:
    ranges = [range_with_height(v0, g, angle, h) for angle in angles]
    plt.plot(angles, ranges, label=f"Height = {h} m")

plt.title("Range vs Angle – Different Launch Heights")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
## 🎯 Range vs Angle (v₀ = 50, 100, 150 m/s)
![Initial Velocities](../images/1.png)
# 🌍 3️⃣ Practical Applications – Real-World Relevance of Projectile Motion

Projectile motion isn't just a classroom example—it’s used in many industries and scientific fields. Below are major real-world applications and extensions of the basic model.

---

## 🏀 Sports

Projectile motion explains the flight paths of balls in sports:

- **Soccer**: A lofted pass or curved free-kick behaves like a projectile.
- **Basketball**: A jump shot’s angle and arc can be optimized for scoring.
- **Golf**: Swing angle and club speed determine the ball’s range and peak height.

Idealized range model:

$$R=\frac{v_0^2\cdot\sin(2\theta)}{g}$$

In reality, air resistance and spin modify this path.

---

## 🏗️ Engineering

Engineering applications include:

- **Ballistics**: Predicting cannon, bullet, or missile trajectories.
- **Robotics**: Calculating parabolic paths for objects thrown by machines.
- **Fireworks**: Designing precise aerial patterns.

To model these realistically, you often include:
- Mass $m$
- Drag force $F_d$
- Initial launch height $h$
- Wind effect

---

## 🚀 Astrophysics

In space, projectile motion generalizes to **orbital mechanics**.

- **Rocket launches** start with projectile-like curves.
- Spacecraft escape velocity depends on trajectory and gravity.

Gravitational variation with height is modeled by:

$$g(h)=\frac{GM}{(R+h)^2}$$

Where:
- $G$: gravitational constant  
- $M$: mass of the planet  
- $R$: planetary radius  
- $h$: altitude

---

## 🌄 Uneven Terrain

In realistic environments:

- Launch and landing points are at **different heights**
- Terrain can be **inclined** or **irregular**

In such cases, the standard range formula fails. You must solve:

$$y(t)=h+v_0\cdot\sin(\theta)\cdot t-\frac{1}{2}gt^2$$

To find $t$ when $y=y_{\text{target}}$, and then:

$$R=v_0\cdot\cos(\theta)\cdot t_{\text{impact}}$$

Numerical root-finding (e.g., Brent’s method) is used.

---

## 🌬️ Air Resistance

Air resistance adds complexity:

$$F_d=\frac{1}{2}C_d\rho Av^2$$

Where:
- $C_d$: drag coefficient  
- $\rho$: air density  
- $A$: cross-sectional area  
- $v$: velocity magnitude

Effects:
- Decreases both range and max height
- Makes path asymmetric

This requires solving a **system of nonlinear differential equations**.

---

## 🌪️ Wind Effects

Wind contributes a horizontal force component:

- Can **increase or decrease** horizontal speed
- Can **push laterally**, affecting direction

Wind modeling often uses:

$$F_{\text{wind}}=m\cdot a_{\text{wind}}$$

Or adjusted velocity:

$$v_{\text{eff}}=v_0\pm v_{\text{wind}}$$

---

## 🌕 Variable Gravity

Gravity isn’t always constant:

- On the **Moon**, $g=1.62$  
- On **Mars**, $g=3.71$  
- High altitudes slightly reduce Earth’s $g$

More accurate gravity model:

$$g(h)=\frac{GM}{(R+h)^2}$$

Used for:
- Rocket reentry  
- Lunar landing  
- Satellite deployment

---

## ✅ Summary

Realistic projectile modeling must include:

- Variable launch/landing heights  
- Gravitational variation  
- Wind and drag  
- Mass and surface area of the object  

The basic model is only a starting point—these factors shape **real-world trajectories** 🌐
# 💻 4️⃣ Implementation – Projectile Motion Simulation in Python

We now implement a simulation to visualize how the **range of a projectile** varies with:
- Launch angle $\theta$
- Initial speed $v_0$
- Gravitational acceleration $g$
- Launch height $h$ (optional)
- Air resistance (optional)

---

## 🎯 Governing Equation

For ideal projectile motion without drag and with flat terrain:

$$R(\theta)=\frac{v_0^2\cdot\sin(2\theta)}{g}$$

---

## 💻 Python Code – Ideal Range Function
```python
import numpy as np
import matplotlib.pyplot as plt

# Ideal range equation
def ideal_range(v0, g, theta_deg):
    theta_rad = np.radians(theta_deg)
    return (v0**2 * np.sin(2 * theta_rad)) / g
angles = np.arange(0, 91, 1)
g = 9.81  # Earth gravity
velocities = [50, 100, 150]  # m/s

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
gravities = [9.81, 1.62]  # Earth and Moon
v0 = 100

plt.figure(figsize=(10, 5))
for g_val in gravities:
    ranges = ideal_range(v0, g_val, angles)
    label = "Earth" if g_val == 9.81 else "Moon"
    plt.plot(angles, ranges, label=f"{label} (g = {g_val} m/s²)")

plt.title("Range vs Angle: Earth vs Moon")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
from scipy.optimize import root_scalar
## 🌍 Earth vs Moon – Same Speed, Different Gravity

Lower gravity (like on the Moon) allows the projectile to stay in air longer → greater range.

![Earth vs Moon](../images/2.png)

def range_with_height(v0, g, theta_deg, h):
    theta_rad = np.radians(theta_deg)
    vy = v0 * np.sin(theta_rad)
    vx = v0 * np.cos(theta_rad)

    def y(t): return h + vy * t - 0.5 * g * t**2

    sol = root_scalar(y, bracket=[0.01, 100], method='brentq')
    t_flight = sol.root
    return vx * t_flight

# Plot for different launch heights
heights = [0, 20, 50]
v0 = 100

plt.figure(figsize=(10, 5))
for h in heights:
    ranges = [range_with_height(v0, g, angle, h) for angle in angles]
    plt.plot(angles, ranges, label=f"Launch Height = {h} m")

plt.title("Range vs Angle with Launch Height")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()


[def]: image.png