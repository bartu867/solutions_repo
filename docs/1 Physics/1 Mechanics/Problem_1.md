## 📘 Family of Solutions from Governing Equations

The motion of a projectile is derived from Newton’s second law. Assuming no air resistance:

- Horizontal motion:  
  \( x(t) = v_0 \cos(\theta) \cdot t \)

- Vertical motion:  
  \( y(t) = v_0 \sin(\theta) \cdot t - \frac{1}{2}gt^2 \)

The time of flight \( T \) is:  
\[
T = \frac{2v_0 \sin(\theta)}{g}
\]

The horizontal range \( R \) becomes:  
\[
R = v_0 \cos(\theta) \cdot T = \frac{v_0^2 \sin(2\theta)}{g}
\]

Each combination of \( v_0 \), \( \theta \), and \( g \) defines a unique solution in the family of projectile trajectories.

---

## 📊 Effect of Parameters on the Range Curve

- **Initial velocity \( v_0 \)**: Directly affects the range quadratically. A higher velocity results in a longer range.
- **Gravitational acceleration \( g \)**: Inversely affects the range. A lower gravity (e.g. Moon) increases the range.
- **Projection angle \( \theta \)**: The range is maximum at 45°, and symmetric about 45° (e.g., 30° and 60° give same range).

These effects can be visualized by altering parameters in the Python simulation.

---

## ⚠️ Limitations of the Idealized Model

- Assumes no air resistance (drag), which is unrealistic in real-world applications.
- Assumes flat ground and constant gravity, ignoring curvature of Earth and altitude changes.
- Does not account for wind or spin of the projectile.

---

## 🧠 Suggestions for a More Realistic Model

- Introduce **air resistance** using a drag force term:  
  \( F_d = -kv \) or \( F_d = -kv^2 \)
- Add **wind effects** as a constant or time-varying horizontal force.
- Include **launch height** or uneven terrain modeling.
- Extend to **2D vector-based simulations** using numerical integration (e.g., Runge-Kutta methods).

