```python
import numpy as np
import matplotlib.pyplot as plt

# Define initial conditions
v0 = 20  # initial velocity in meters per second
g = 9.81  # gravitational acceleration in meters per second squared

# Create a list of launch angles from 0 to 90 degrees
angles = np.linspace(0, 90, 500)  # angle values in degrees
radians = np.radians(angles)  # convert degrees to radians

# Calculate the horizontal range for each angle
range_values = (v0**2) * np.sin(2 * radians) / g

# Plot the range as a function of launch angle
plt.figure(figsize=(10, 5))
plt.plot(angles, range_values, color="blue", linewidth=2)
plt.title("Range as a Function of Launch Angle")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)
plt.tight_layout()
plt.show()
