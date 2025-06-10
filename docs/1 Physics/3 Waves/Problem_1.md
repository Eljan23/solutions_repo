**Problem 1: Interference Patterns on a Water Surface**

---

### 🔹 Mathematical Model

The wave from a single point source is given by:

$$
\eta(x, y, t) = A \sin(kr - \omega t + \phi)
$$

Where:

* $A$: Amplitude
* $r = \sqrt{(x - x_0)^2 + (y - y_0)^2}$: Distance from the source
* $k = \frac{2\pi}{\lambda}$: Wave number
* $\omega = 2\pi f$: Angular frequency
* $\phi$: Initial phase

The total displacement from $N$ sources becomes:

$$
\eta_{\text{total}}(x, y, t) = \sum_{i=1}^{N} A \sin(k r_i - \omega t + \phi)
$$

---

### 🔹 Python Code

```python
import numpy as np
import matplotlib.pyplot as plt

# Simulation Parameters
A = 1.0
wavelength = 1.0
frequency = 1.0
k = 2 * np.pi / wavelength
omega = 2 * np.pi * frequency
phi = 0
t = 0

# Grid setup
x = np.linspace(-5, 5, 500)
y = np.linspace(-5, 5, 500)
X, Y = np.meshgrid(x, y)

# Regular Polygon: Square (4 vertices)
n_sources = 4
radius = 2.0
angles = np.linspace(0, 2*np.pi, n_sources, endpoint=False)
source_positions = [(radius * np.cos(a), radius * np.sin(a)) for a in angles]

# Interference pattern
Z = np.zeros_like(X)
for x0, y0 in source_positions:
    r = np.sqrt((X - x0)**2 + (Y - y0)**2)
    Z += A * np.sin(k * r - omega * t + phi)

# Plotting
plt.figure(figsize=(8, 6))
plt.contourf(X, Y, Z, levels=100, cmap='RdBu')
plt.colorbar(label='Displacement')
plt.title('Interference Pattern from 4 Point Sources (Square Configuration)')
plt.xlabel('x')
plt.ylabel('y')
plt.axis('equal')
plt.tight_layout()
plt.show()
```
![alt text](image-4.png)
---

