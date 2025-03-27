# Problem 1
# Problem 1 – Investigating the Range as a Function of the Angle of Projection

## 🎯 Amaç
Fırlatma açısına göre menzilin nasıl değiştiğini incelemek.

---

## 📘 Teorik Arka Plan
Bir cismin yatay menzili şu formülle verilir:

\[
R = \frac{v_0^2 \cdot \sin(2\theta)}{g}
\]

Burada:
- \( R \): menzil
- \( v_0 \): ilk hız
- \( \theta \): fırlatma açısı
- \( g = 9.81 \, m/s^2 \): yerçekimi ivmesi

---

## 💻 Python Simülasyonu

```python
import numpy as np
import matplotlib.pyplot as plt

# Parametreler
v0 = 20  # m/s
g = 9.81
angles = np.linspace(0, 90, 500)
radians = np.radians(angles)

# Menzil hesaplama
range_values = (v0**2) * np.sin(2 * radians) / g

# Grafik çizimi
plt.figure(figsize=(10,5))
plt.plot(angles, range_values)
plt.title("Fırlatma Açısına Göre Menzil")
plt.xlabel("Açı (derece)")
plt.ylabel("Menzil (m)")
plt.grid(True)
plt.show()

