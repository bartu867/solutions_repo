# 🛰️ Problem 3 – Trajectories of a Freely Released Payload Near Earth

**Physics** | **Gravity** | **KW1 Assignment**  
**Author:** Bartu867  
**Date:** March 29, 2025

---
# Problem 3
## Theoretical Foundation

### Newton’s Law of Gravitation

- Newton's Law of Universal Gravitation states that any two masses in the universe attract each other with a force given by:

$$F=G\frac{m_1m_2}{r^2}$$

  where:
- $F$ is the gravitational force,

- $G$ is the gravitational constant ($6.674\times10^{-11}$ m²/kg²)

- $m_1,m_2$ are the masses of the two objects,

- $r$ is the distance between the objects.

- For a payload near Earth, the force simplifies to:

$$F=G\frac{M_Em}{r^2}$$

  where $M_E$ is Earth's mass and $r$ is the distance from Earth's center.

- The acceleration due to gravity is:

$$g=\frac{GM_E}{r^2}$$

  which varies with altitude.
### Kepler’s Laws of Planetary Motion

1. **First Law (Elliptical Orbits)**: Planets move in ellipses with the Sun at one focus. Similarly, a payload follows an elliptical, parabolic, or hyperbolic path based on its initial velocity.

2. **Second Law (Equal Areas in Equal Time)**: The line joining a planet and the Sun sweeps equal areas in equal time. This implies that an object moves faster when closer to Earth.

3. **Third Law (Orbital Period Relation)**: The square of a planet’s orbital period is proportional to the cube of the semi-major axis:

$$T^2\propto a^3$$

 This helps in predicting orbital parameters.

### Classification of Possible Trajectories

- The motion of a payload depends on its total energy:

$$E=\frac{1}{2}mv^2-\frac{GM_Em}{r}$$

- If $E<0$ → **Elliptical orbit** (Bound motion)

- If $E=0$ → **Parabolic trajectory** (Escape condition)

- If $E>0$ → **Hyperbolic trajectory** (Unbound motion)

- The escape velocity is given by:

$$v_{esc}=\sqrt{\frac{2GM_E}{r}}$$

### Conditions for Orbital Insertion, Reentry, or Escape

- **Orbital Insertion**:
- Requires achieving a velocity that results in a stable bound orbit.
- For a circular orbit at altitude $h$:

$$v_{orbit}=\sqrt{\frac{GM_E}{R_E+h}}$$
  
- **Reentry Conditions**:
  - A payload must reduce velocity to enter the atmosphere.
  - Atmospheric drag plays a key role in slowing it down.

- **Escape Trajectories**:
  - If velocity exceeds escape velocity, the payload follows a hyperbolic trajectory away from Earth.

This theoretical background lays the foundation for numerical simulations of payload trajectories.
---


## Mathematical Formulation

### Equations of Motion for a Payload under Earth's Gravity

- The motion of a payload is governed by Newton’s Second Law:

$$F=ma$$

  Since the only force acting is gravity:

$$m\frac{d^2\mathbf{r}}{dt^2}=-G\frac{M_Em}{r^2}\hat{r}$$

  Simplifying:

$$\frac{d^2\mathbf{r}}{dt^2}=-G\frac{M_E}{r^2}\hat{r}$$
- In Cartesian coordinates:

$$\frac{d^2x}{dt^2}=-G\frac{M_E}{r^3}x$$

$$\frac{d^2y}{dt^2}=-G\frac{M_E}{r^3}y$$

$$\frac{d^2z}{dt^2}=-G\frac{M_E}{r^3}z$$

where $r=\sqrt{x^2+y^2+z^2}$.

### Consideration of Initial Velocity, Altitude, and Direction

- Initial position:

$$\mathbf{r_0}=(x_0,y_0,z_0)$$

- Initial velocity:

$$\mathbf{v_0}=(v_{x0},v_{y0},v_{z0})$$

- The trajectory depends on:

  - Magnitude and direction of $\mathbf{v_0}$.

  - The altitude ($h$) from the Earth's surface: 

$$r_0=R_E+h$$

### Criteria for Different Trajectories

- The total specific energy determines the trajectory:
$$E=\frac{1}{2}v^2-\frac{GM_E}{r}$$

- If $E<0$: **Elliptical orbit** (Bound motion)

- If $E=0$: **Parabolic trajectory** (Escape condition)

- If $E>0$: **Hyperbolic trajectory** (Unbound motion)

- Escape velocity condition:

$$v_0\geq\sqrt{\frac{2GM_E}{r_0}}$$

  ensures that the payload escapes Earth's gravitational influence.

This mathematical formulation establishes the foundation for numerical simulations of payload motion.
---

## Numerical Simulation

### Implement a Python Script to Solve the Equations of Motion

We solve the equations of motion numerically using an appropriate method such as the Runge-Kutta method. The equations of motion are:

$$
m \frac{d^2 \mathbf{r}}{dt^2} = - G \frac{M_E m}{r^2} \hat{r}
$$

This simplifies to:

$$
\frac{d^2 \mathbf{r}}{dt^2} = - G \frac{M_E}{r^2} \hat{r}
$$
To implement this, we break it down into first-order differential equations by defining velocity as:

$$
\mathbf{v} = \frac{d \mathbf{r}}{dt}
$$

Thus, we can write the system of equations as:

$$
\frac{d \mathbf{r}}{dt} = \mathbf{v}
$$

$$
\frac{d \mathbf{v}}{dt} = - G \frac{M_E}{r^2} \hat{r}
$$

### Use Numerical Methods (e.g., Runge-Kutta) for Trajectory Calculations

- The Runge-Kutta method is an efficient and accurate way to numerically solve these differential equations. The fourth-order Runge-Kutta method (RK4) is commonly used for its balance between complexity and accuracy.

Let the system of differential equations be represented as:

$$
\mathbf{r}' = \mathbf{v}
$$

$$
\mathbf{v}' = - G \frac{M_E}{r^2} \hat{r}
$$

The Runge-Kutta method will numerically integrate these equations step-by-step, providing the trajectory of the payload over time.

### Account for Different Initial Conditions

We consider various initial conditions, such as:

- Initial position:

$$
\mathbf{r_0} = (x_0, y_0, z_0)
$$

- Initial velocity:

$$
\mathbf{v_0} = (v_{x0}, v_{y0}, v_{z0})
$$

The trajectory depends on the magnitude and direction of the initial velocity and the altitude:

$$
r_0 = R_E + h
$$
### Python Implementation

The following Python code can be used to solve these equations using the Runge-Kutta method:

![alt text](image-3.png)

```python
import numpy as np
import matplotlib.pyplot as plt
```
# Constants
G = 6.67430e-11  # gravitational constant (m^3 kg^-1 s^-2)
M_E = 5.972e24   # Earth's mass (kg)
R_E = 6371000    # Earth's radius (m)
```
# Initial conditions
r0 = np.array([R_E + 100000, 0, 0])  # 100 km above Earth's surface
v0 = np.array([0, 7800, 0])          # orbital velocity in m/s
```
# Time parameters
t_max = 5000  # total simulation time in seconds
dt = 1        # time step in seconds
```
# Runge-Kutta integrator
def runge_kutta_step(r, v, dt):
    r_mag = np.linalg.norm(r)
    if r_mag < R_E:
        raise ValueError("Object has collided with Earth!")
    
    a = -G * M_E * r / r_mag**3
    k1v, k1r = dt * a, dt * v
    r2, v2 = r + 0.5 * k1r, v + 0.5 * k1v

    a2 = -G * M_E * r2 / np.linalg.norm(r2)**3
    k2v, k2r = dt * a2, dt * v2
    r3, v3 = r + 0.5 * k2r, v + 0.5 * k2v

    a3 = -G * M_E * r3 / np.linalg.norm(r3)**3
    k3v, k3r = dt * a3, dt * v3
    r4, v4 = r + k3r, v + k3v

    a4 = -G * M_E * r4 / np.linalg.norm(r4)**3
    k4v, k4r = dt * a4, dt * v4

    v_next = v + (k1v + 2 * k2v + 2 * k3v + k4v) / 6
    r_next = r + (k1r + 2 * k2r + 2 * k3r + k4r) / 6
    return r_next, v_next
```
# Simulation loop
r, v = r0, v0
positions = []

for t in np.arange(0, t_max, dt):
    positions.append(r)
    try:
        r, v = runge_kutta_step(r, v, dt)
    except ValueError as e:
        print(e)
        break
positions = np.array(positions)

# Plotting
fig, ax = plt.subplots(figsize=(8, 8))
ax.plot(positions[:, 0], positions[:, 1], label="Trajectory", color='blue')

# Draw Earth as a red circle
earth = plt.Circle((0, 0), R_E, color='red', label='Earth', alpha=0.6)
ax.add_patch(earth)

ax.set_title('Trajectory of the Payload')
ax.set_xlabel('X position (m)')
ax.set_ylabel('Y position (m)')
ax.set_aspect('equal')
ax.legend()
ax.grid(True)
plt.show()
```
---
```
### Generate Plots for Various Payload Trajectories

To visualize the payload's motion, we generate several plots that help analyze the behavior of the trajectory. The primary visualizations include:

- Time evolution of position and velocity.
- Phase space diagrams.
- Orbit visualizations.

### Time Evolution of Position and Velocity

We can plot the time evolution of the payload's position and velocity over time to understand how they change as the payload moves under Earth's gravitational influence. 

### Phase Space Diagrams

A phase space diagram shows the relationship between position and velocity. For a two-dimensional system, we can plot the position in the x-direction versus the velocity in the x-direction, and similarly for the y and z components.

### Orbit Visualizations

We can visualize the payload's orbit as it moves through space. This plot will show the path in 3D space, displaying the orbital trajectory relative to Earth.

### Additional Analysis

In addition to the plots above, other analyses could include:

- **Energy plots**: Tracking the total mechanical energy (kinetic + potential) over time to check for conservation.
- **Orbital insertion analysis**: Determining whether the payload is in a bound orbit or has escaped Earth’s gravitational influence.

### Conclusion
These visualizations help to better understand the motion of the payload under the influence of gravity. By examining the time evolution of position and velocity, phase space diagrams, and orbit visualizations, we can gain insights into the nature of the trajectory, whether elliptical, hyperbolic, or parabolic.

![alt text](image-4.png)

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp
```
# Constants
G = 6.67430e-11  # Gravitational constant (m^3 kg^-1 s^-2)
M = 5.972e24     # Mass of Earth (kg)
R_earth = 6371e3  # Radius of Earth (m)

# Initial position (on Earth's surface)
r0 = np.array([R_earth, 0])
magnitude_r0 = np.linalg.norm(r0)

# Time span for simulation (seconds)
t_span = (0, 6000)
t_eval = np.linspace(*t_span, 2000)

# Velocities to simulate (m/s)
velocities = [9000, 10000, 11000, 11200, 11250]
colors = ['gold', 'orange', 'crimson', 'violet', 'deepskyblue']

def gravity(t, state):
    x, y, vx, vy = state
    r = np.sqrt(x**2 + y**2)
    ax = -G * M * x / r**3
    ay = -G * M * y / r**3
    return [vx, vy, ax, ay]

# Plot setup
fig, ax = plt.subplots(figsize=(8, 8))

for v0, color in zip(velocities, colors):
    # Initial velocity vector (tangential, upward from surface)
    vx0 = 0
    vy0 = v0
    initial_state = [r0[0], r0[1], vx0, vy0]

    sol = solve_ivp(gravity, t_span, initial_state, t_eval=t_eval, rtol=1e-8)

    x = sol.y[0] / 1000  # convert to km
    y = sol.y[1] / 1000  # convert to km
    ax.plot(x, y, color=color, label=f'v = {v0} m/s')

# Draw Earth
earth = plt.Circle((0, 0), R_earth/1000, color='blue', alpha=0.3)
ax.add_patch(earth)

# Labels and legend
ax.set_xlabel("x (km)")
ax.set_ylabel("y (km)")
ax.set_title("Case 4: Near-Escape velocities", fontsize=14, weight='bold')
ax.set_aspect('equal')
ax.grid(True)
ax.legend()
plt.tight_layout()
plt.show()

```

## Real-World Applications
```
### Relevance to Space Missions and Satellite Deployment

The study of payload trajectories is essential for various space missions, particularly those involving satellite deployment, payload release, or reentry. The trajectory analysis helps in determining:

- **Orbital Insertion**: The process of placing a satellite into orbit requires a precise calculation of the velocity and trajectory, ensuring that the payload reaches the correct altitude and orbital velocity.
- **Satellite Deployment**: When deploying satellites from a spacecraft, the release velocity and angle must be carefully chosen to ensure that the satellite remains in orbit or follows the intended path.
  
  The velocity required for an object to maintain a stable orbit around Earth is determined by the following equation:

  $$
  v = \sqrt{\frac{GM_E}{r}}
  $$

  Where:
  - $G$ is the gravitational constant,

  - $M_E$ is Earth's mass,

  - $r$ is the orbital radius (distance from Earth's center).
  The altitude at which the payload is released, and its initial velocity, are critical for the success of satellite deployment. If the velocity is too low, the satellite will fall back to Earth. If the velocity is too high, the satellite may escape Earth's gravity.

### Reentry Strategies

Reentry into Earth's atmosphere requires precise control of the payload's trajectory to ensure it slows down enough to avoid burning up due to friction. The conditions for reentry are influenced by:

- **Orbital Decay**: Over time, satellites in low Earth orbit experience atmospheric drag, which causes their orbits to decay, eventually leading to reentry.
- **Reentry Angle**: The angle at which a spacecraft reenters the atmosphere affects the amount of heat and stress it experiences. A shallow reentry angle may cause the spacecraft to skip off the atmosphere, while a steep angle may lead to rapid deceleration and heat buildup.

The critical speed required to escape Earth's gravity is called the **escape velocity**, and is given by:

$$
v_{esc} = \sqrt{\frac{2GM_E}{r}}
$$

Where:
- $v_{esc}$ is the escape velocity,

- $G$ is the gravitational constant,

- $M_E$ is Earth's mass,

- $r$ is the distance from Earth's center.
The altitude at which the payload is released, and its initial velocity, are critical for the success of satellite deployment. If the velocity is too low, the satellite will fall back to Earth. If the velocity is too high, the satellite may escape Earth's gravity.

### Reentry Strategies

Reentry into Earth's atmosphere requires precise control of the payload's trajectory to ensure it slows down enough to avoid burning up due to friction. The conditions for reentry are influenced by:

- **Orbital Decay**: Over time, satellites in low Earth orbit experience atmospheric drag, which causes their orbits to decay, eventually leading to reentry.
- **Reentry Angle**: The angle at which a spacecraft reenters the atmosphere affects the amount of heat and stress it experiences. A shallow reentry angle may cause the spacecraft to skip off the atmosphere, while a steep angle may lead to rapid deceleration and heat buildup.

The critical speed required to escape Earth's gravity is called the **escape velocity**, and is given by:

$$
v_{esc} = \sqrt{\frac{2GM_E}{r}}
$$

Where:
- $v_{esc}$ is the escape velocity,

- $G$ is the gravitational constant,

- $M_E$ is Earth's mass,

- $r$ is the distance from Earth's center.

The concepts of escape velocity, orbital insertion, and trajectory analysis are foundational in space exploration and satellite deployment. Understanding these principles allows for the successful launch, deployment, and reentry of payloads, making them vital for future space missions, including Mars exploration, lunar missions, and the growing field of satellite-based communications and earth observation.