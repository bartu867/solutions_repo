# 🔬 Physics Assignment – KW1  
**Topic:** Mechanics – Oscillations & Motion  
**Author:** Bartu867  
**Date:** March 27, 2025  

# Problem 2

# 📚 Theoretical Foundation of the Forced Damped Pendulum

## 1️⃣ Formulating the Differential Equation for the Forced Damped Pendulum ⚖️

The motion of a forced damped pendulum can be described using Newton's Second Law:

$$mL\frac{d^2\theta}{dt^2}+b\frac{d\theta}{dt}+mg\sin\theta=F_0\cos(\omega t)$$

where:
- $m$ is the mass of the pendulum,
- $L$ is the length of the pendulum,
- $b$ is the damping coefficient,
- $g$ is the acceleration due to gravity,
- $F_0$ is the amplitude of the external driving force,
- $\omega$ is the driving frequency,
- $\theta$ is the angular displacement.

Dividing through by $mL$:

$$\frac{d^2\theta}{dt^2}+\frac{b}{mL}\frac{d\theta}{dt}+\frac{g}{L}\sin\theta=\frac{F_0}{mL}\cos(\omega t)$$

To make the equation more manageable, we define dimensionless parameters:
- $\gamma=\frac{b}{mL}$ (damping ratio, representing the effect of friction),
- $\omega_0^2=\frac{g}{L}$ (square of the natural frequency, characterizing the system's oscillation rate),
- $f=\frac{F_0}{mL}$ (scaled external force).

This leads to the simplified equation:

$$\ddot{\theta}+\gamma\dot{\theta}+\omega_0^2\sin\theta=f\cos(\omega t)$$

![alt text](image-15.png)

## 2️⃣ Approximate Solutions for Small-Angle Oscillations 🔬

For small angles ($\theta\approx\sin\theta$), we can linearize the equation:

$$\ddot{\theta}+\gamma\dot{\theta}+\omega_0^2\theta=f\cos(\omega t)$$

This equation describes a **damped, driven harmonic oscillator**. Using the method of undetermined coefficients, we assume the steady-state solution is of the form:

$$\theta(t)=A\cos(\omega t-\delta)$$

where:

- **Amplitude** $A$ determines the system's response to the driving force:
  
  $$A=\frac{f}{\sqrt{(\omega_0^2-\omega^2)^2+\gamma^2\omega^2}}$$

- **Phase shift** $\delta$ accounts for the lag due to damping:
  
  $$\tan\delta=\frac{\gamma\omega}{\omega_0^2-\omega^2}$$

This means the oscillations **lag behind the external force**, with the delay increasing as damping grows.

## 3️⃣ Analysis of Resonance Conditions and Energy Impact 🎵⚡

### 🌟 Resonance: When the System Responds Most Strongly

Resonance occurs when the driving frequency matches the system's natural frequency:

$$\omega\approx\omega_0$$

At this point, the denominator of $A$ approaches zero, leading to a **large increase in oscillation amplitude**. In real-world systems, damping prevents infinite amplitude but still allows significant oscillations.

### 🔋 Energy Considerations
The total mechanical energy of the pendulum consists of kinetic and potential energy:

$$E=T+U=\frac{1}{2}mL^2\dot{\theta}^2+mgL(1-\cos\theta)$$

For small oscillations, this simplifies to:

$$E\approx\frac{1}{2}mL^2\dot{\theta}^2+\frac{1}{2}mgL\theta^2$$

Under steady-state forced oscillations, energy input from the external force **balances** the dissipation due to damping. This results in a periodic exchange of energy within the system.

---
## 📌 Summary 📝
- The forced damped pendulum obeys a nonlinear differential equation, which simplifies under small-angle assumptions.
- Its behavior is characterized by damping, external driving forces, and resonance effects.
- Resonance occurs when the driving frequency approaches the natural frequency, leading to large oscillations.
- The system's energy oscillates due to an external force counteracting damping losses.

These principles are crucial in engineering, physics, and even biological systems (e.g., heart rhythms, bridges swaying). Understanding them helps in designing **stable** and **efficient** mechanical systems! 🚀

# 🔍 Analysis of Dynamics

## ⚖️ 2.1 Influence of Damping Coefficient

The equation of motion for a damped driven system is given by:

$$m\ddot{x} + b\dot{x} + kx = F_0\cos(\omega t)$$

where:
- $m$ is the mass of the system, determining inertia.
- $b$ is the damping coefficient, controlling resistance to motion.
- $k$ is the spring constant, representing restoring force.
- $F_0$ is the external driving amplitude.
- $\omega$ is the driving frequency.

### 🔬 Types of Damping
- **Underdamping** ($b^2<4mk$): System oscillates with decreasing amplitude over time.
- **Critical damping** ($b^2=4mk$): System returns to equilibrium as fast as possible without oscillating.
- **Overdamping** ($b^2>4mk$): System slowly returns to equilibrium without oscillation.

The **quality factor** $Q$ measures how underdamped a system is:

$$Q=\frac{m\omega_0}{b}$$

where $\omega_0=\sqrt{k/m}$ is the natural frequency. High $Q$ means low damping and more oscillations.

## 📈 2.2 Influence of Driving Amplitude

When the system is driven externally, the steady-state amplitude follows:

$$A=\frac{F_0/m}{\sqrt{(\omega_0^2-\omega^2)^2+(b\omega/m)^2}}$$

- **Small $F_0$:** Response is proportional to the force (linear behavior).
- **At resonance ($\omega=\omega_0$):** Amplitude reaches a peak.
- **High $F_0$:** Nonlinear effects and potential chaotic motion emerge.

## 🎶 2.3 Influence of Driving Frequency

The system's response changes with frequency $\omega$:
- **Low-frequency regime** ($\omega\ll\omega_0$): The system follows the driving force smoothly.
- **Near resonance** ($\omega\approx\omega_0$): Maximum amplitude occurs due to resonance.
- **High-frequency regime** ($\omega\gg\omega_0$): The system cannot keep up with the driving force, resulting in reduced response.

The phase lag $\phi$ between the driving force and displacement is:

$$\tan\phi=\frac{b\omega}{m(\omega_0^2-\omega^2)}$$

## 🔀 2.4 Transition Between Regular and Chaotic Motion

For nonlinear driven systems, such as the Duffing oscillator:

$$m\ddot{x} + b\dot{x} + kx + \alpha x^3 = F_0\cos(\omega t)$$

where $\alpha$ introduces nonlinearity. The system can exhibit:
- **Periodic motion**: Regular oscillations with predictable behavior.
- **Quasiperiodic motion**: Oscillations with multiple incommensurate frequencies.
- **Chaotic motion**: Unpredictable behavior with extreme sensitivity to initial conditions.

### 📊 Lyapunov Exponent
A key indicator of chaos is the Lyapunov exponent $\lambda$:

$$\lambda=\lim_{t\to\infty} \frac{1}{t} \ln \frac{|\delta x(t)|}{|\delta x(0)|}$$

- If $\lambda>0$, the system is **chaotic**.
- If $\lambda<0$, the system is **stable and predictable**.

### 🌀 Poincaré Section
A visualization technique for chaos:
- **Regular motion** forms closed loops.
- **Chaotic motion** forms scattered, fractal-like structures.

## 🌍 2.5 Physical Significance
- **🚗 Engineering:** Used in shock absorbers and mechanical resonance analysis.
- **🌦️ Climate Models:** Helps predict weather patterns and turbulence.
- **🧠 Biological Systems:** Found in heart rhythms and neural oscillations.
- **🪐 Astronomy:** Governs planetary motion, stability, and celestial mechanics.
---
### 📝 Summary
- The behavior of oscillatory systems depends on damping, driving force, and frequency.
- Resonance amplifies oscillations but can also lead to instability.
- Nonlinearities introduce complex behaviors, including chaos.
- Chaos is characterized by sensitivity to initial conditions, analyzed via Lyapunov exponents and Poincare sections.

This document provides a detailed mathematical and conceptual framework for analyzing dynamical systems, emphasizing the transition from **order to chaos**.

# 🔬 Practical Applications of Oscillatory Systems ⚙️

Oscillatory systems play a crucial role in various engineering and scientific disciplines, governing the behavior of mechanical structures, electrical circuits, and energy harvesting technologies. By understanding these systems, engineers can design safer bridges, efficient energy systems, and optimized electronic devices. This section explores some key real-world applications, including energy harvesting, suspension bridges, and oscillating circuits.

## ⚡ 1. Energy Harvesting

Energy harvesting technologies utilize oscillatory and vibrational motions to generate electrical energy from ambient sources such as vibrations, thermal fluctuations, or mechanical motion. These systems often employ piezoelectric, electromagnetic, or electrostatic transduction mechanisms.

The governing equation for a simple electromechanical energy harvester is given by:

$$m\ddot{x}+c\dot{x}+kx=F_{ext}(t)$$

where:
- $m$ is the mass of the oscillating system,
- $c$ is the damping coefficient,
- $k$ is the stiffness constant,
- $F_{ext}(t)$ represents the external excitation force.

By incorporating an electromechanical coupling term, the output voltage $V$ across a piezoelectric material is given by:

$$V=\frac{d_{31}F_{ext}(t)}{C_p}$$

where:
- $d_{31}$ is the piezoelectric charge constant,
- $C_p$ is the capacitance of the piezoelectric element.

**Applications:**

- Powering remote sensors in industrial and environmental monitoring.

- Harvesting kinetic energy from human motion for wearable electronics.

- Utilizing ocean wave energy for renewable power generation.

##  2. Suspension Bridges

Suspension bridges are subject to oscillatory forces from wind, traffic loads, and seismic activity. The famous case of the **Tacoma Narrows Bridge collapse** in 1940 illustrates the importance of understanding resonance effects in structural engineering.

The equation governing small oscillations of a bridge modeled as a beam is:

$$EI\frac{\partial^4 y}{\partial x^4}+m\frac{\partial^2 y}{\partial t^2}+c\frac{\partial y}{\partial t}=F_{wind}(t)$$

where:
- $E$ is Young’s modulus (material stiffness),
- $I$ is the second moment of area (beam shape factor),
- $m$ is the mass per unit length,
- $c$ is the damping coefficient,
- $F_{wind}(t)$ represents wind-induced forcing.

For stability, damping must be introduced to prevent resonance when the natural frequency $\omega_n$ matches the forcing frequency:

$$\omega_n=\sqrt{\frac{k}{m}}$$

**Applications:**
- Design of earthquake-resistant bridges.
- Optimization of bridge materials to reduce vibration amplitudes.
- Wind tunnel testing for aerodynamically stable structures.

##  3. Oscillating Circuits

Electrical circuits containing inductors, capacitors, and resistors exhibit oscillatory behavior essential in communication systems, signal processing, and power electronics. The standard RLC circuit equation follows from Kirchhoff’s voltage law:

$$L\frac{d^2 q}{d t^2}+R\frac{d q}{d t}+\frac{q}{C}=0$$

where:
- $L$ is the inductance,
- $R$ is the resistance,
- $C$ is the capacitance,
- $q$ is the charge on the capacitor.

The characteristic equation of the circuit is:

$$s^2+\frac{R}{L}s+\frac{1}{LC}=0$$

Solving for $s$, the damping factor $\zeta$ determines whether the circuit is overdamped, underdamped, or critically damped:

$$\zeta=\frac{R}{2}\sqrt{\frac{C}{L}}$$

**Applications:**
- Design of radio frequency (RF) filters in communication devices.
- Stability analysis of power supply circuits.
- Development of resonant transformers and wireless charging systems.

##  Summary

Oscillatory systems are fundamental to many engineering applications, from structural mechanics to electronic circuit design and renewable energy solutions. Understanding their behavior through mathematical modeling allows for the **optimization of structures and devices** ,ensuring:
✅ Stability against external perturbations.
✅ Efficiency in energy conversion processes.
✅ Performance improvement in electronic and mechanical systems.

By mastering the principles of oscillatory dynamics, engineers and scientists can develop **safer, more efficient, and innovative** solutions to real-world challenges.

![alt text](image-16.png)
![alt text](image-17.png)

## Python/ plot

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Define the pendulum parameters
g = 9.81  # Gravity (m/s^2)
L = 1.0   # Length of pendulum (m)
m = 1.0   # Mass (kg)
F0 = 1.5  # Driving force amplitude
omega = 2.0  # Driving frequency

# Define the equation of motion
def forced_damped_pendulum(t, y, gamma, omega_0, f, omega):
    theta, omega_theta = y
    dydt = [
        omega_theta,
        -gamma * omega_theta - omega_0**2 * np.sin(theta) + f * np.cos(omega * t)
    ]
    return dydt

# Time span and initial conditions
t_span = (0, 20)
t_eval = np.linspace(*t_span, 1000)
y0 = [np.pi / 4, 0]  # Initial angle and velocity

# Define damping cases
damping_cases = {
    "Underdamped": 0.5,
    "Critically Damped": 2.0,
    "Overdamped": 5.0
}

# Solve and plot for each case
plt.figure(figsize=(12, 8))
for i, (label, gamma) in enumerate(damping_cases.items(), 1):
    omega_0 = np.sqrt(g / L)
    f = F0 / (m * L)
    
    sol = solve_ivp(forced_damped_pendulum, t_span, y0, t_eval=t_eval, args=(gamma, omega_0, f, omega))
    
    # Extract solutions
    theta, omega_theta = sol.y
    
    # Phase diagram
    plt.subplot(1, 3, i)
    plt.plot(theta, omega_theta, label=label)
    plt.xlabel("Theta (rad)")
    plt.ylabel("Angular Velocity (rad/s)")
    plt.title(f"Phase Diagram ({label})")
    plt.legend()
    plt.grid()

plt.tight_layout()
plt.show()
```
![alt text](image-18.png)