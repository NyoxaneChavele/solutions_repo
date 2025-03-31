# Problem 2
# **Investigating the Dynamics of a Forced Damped Pendulum**  

## **Introduction & Motivation**  
The **forced damped pendulum** is a fascinating example of how simple physical systems can exhibit highly complex behavior. By introducing both **damping** and an **external periodic force**, this system transitions from predictable harmonic motion to intricate dynamics such as **resonance, quasiperiodic oscillations, and even chaos**.  

Understanding these behaviors is crucial for various real-world applications, from **mechanical oscillators** and **bridge dynamics** to **biomechanics** and **electrical circuits**. This report delves into the governing equations, solutions, and computational simulations to explore the pendulum's rich dynamical landscape.  

## **Theoretical Foundation**  

### **Governing Equation**  
The motion of a forced damped pendulum is governed by the **second-order nonlinear differential equation**:  

$$
\frac{d^2\theta}{dt^2} + b \frac{d\theta}{dt} + \frac{g}{L} \sin\theta = A \cos(\omega t)
$$

where:  
- $\theta$ is the angular displacement,  
- $b$ is the damping coefficient,  
- $g$ is the acceleration due to gravity,  
- $L$ is the length of the pendulum,  
- $A$ is the amplitude of the external forcing, and  
- $\omega$ is the driving frequency.  

### **Small-Angle Approximation**  
For small angles ($\theta \approx 0$), we approximate **$\sin\theta \approx \theta$**, simplifying the equation to:  

$$
\frac{d^2\theta}{dt^2} + b \frac{d\theta}{dt} + \frac{g}{L} \theta = A \cos(\omega t)
$$

This approximation allows analytical solutions, but for **larger angles and chaotic behavior**, numerical methods are required.  

## **Analysis of Dynamics**  

### **Effect of Damping & Driving Forces**  
- **Low damping** ($b \approx 0$) → Near-harmonic motion, with oscillations resembling a simple pendulum.  
- **High damping** ($b \gg 1$) → Motion dies out quickly unless sustained by the external force.  
- **Varying driving amplitude $A$ and frequency $\omega$** leads to **resonance** or **chaotic motion**.  

### **Regular vs. Chaotic Motion**  
By systematically varying parameters, we observe:  
- **Regular Motion:** Predictable oscillations at low forcing amplitudes.  
- **Chaotic Motion:** Sensitive dependence on initial conditions, leading to **unpredictable long-term behavior**.  

A deeper look at these transitions requires **phase portraits** and **Poincaré sections**, which we analyze computationally.  

## **Practical Applications**  

The forced damped pendulum is not just a theoretical construct—it has **real-world significance**, including:  
- **Energy Harvesting**: Capturing oscillatory energy for sustainable power solutions.  
- **Bridge Dynamics**: Preventing resonance-induced collapses (e.g., Tacoma Narrows Bridge).  
- **Biomechanics**: Modeling human gait and posture control.  
- **Electronics**: Analogous to **driven RLC circuits**, influencing circuit resonance and stability.  

## **Implementation & Simulations**  

To visualize the pendulum’s motion under different conditions, we implement a **numerical simulation using Python** with the **Runge-Kutta method**.  

### **Python Code for Simulation**  

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Define system parameters
b = 0.5     # Damping coefficient
A = 1.2     # Driving force amplitude
omega = 2.0 # Driving frequency
g = 9.81    # Gravity
L = 1.0     # Pendulum length

# Define the differential equation
def pendulum_eq(t, y):
    theta, omega_t = y
    dtheta_dt = omega_t
    domega_dt = -b * omega_t - (g/L) * np.sin(theta) + A * np.cos(omega * t)
    return [dtheta_dt, domega_dt]

# Initial conditions
y0 = [0.2, 0.0]  # Small initial angle, no initial velocity
t_span = (0, 50) # Time span
t_eval = np.linspace(t_span[0], t_span[1], 1000)

# Solve the ODE
solution = solve_ivp(pendulum_eq, t_span, y0, t_eval=t_eval, method='RK45')

# Plot the results
plt.figure(figsize=(10,5))
plt.plot(solution.t, solution.y[0], label="Theta (angle)")
plt.xlabel("Time (s)")
plt.ylabel("Angular Displacement (rad)")
plt.title("Forced Damped Pendulum Motion")
plt.legend()
plt.grid()
plt.show()
```
<a href="https://colab.research.google.com/drive/1ED2QsXcYoWrW_lvZAib4xwUUv1mC7xLr?usp=sharing" target="_blank">Colab</a>

## **Advanced Visualization Techniques**  

### **Phase Portraits**  
Plotting **angular velocity vs. displacement** to observe stable and chaotic regimes.  


```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Define system parameters
b = 0.5     # Damping coefficient
A = 1.2     # Driving force amplitude
omega = 2.0 # Driving frequency
g = 9.81    # Gravity
L = 1.0     # Pendulum length

# Define the differential equation
def pendulum_eq(t, y):
    theta, omega_t = y
    dtheta_dt = omega_t
    domega_dt = -b * omega_t - (g/L) * np.sin(theta) + A * np.cos(omega * t)
    return [dtheta_dt, domega_dt]

# Initial conditions
y0 = [0.2, 0.0]  # Small initial angle, no initial velocity
t_span = (0, 50) # Time span
t_eval = np.linspace(t_span[0], t_span[1], 1000)

# Solve the ODE
solution = solve_ivp(pendulum_eq, t_span, y0, t_eval=t_eval, method='RK45')

# Plot the phase portrait (Angular Displacement vs. Angular Velocity)
plt.figure(figsize=(8,5))
plt.plot(solution.y[0], solution.y[1], label="Phase Portrait", color='b')
plt.xlabel("Theta (rad)")
plt.ylabel("Angular Velocity (rad/s)")
plt.title("Phase Portrait of Forced Damped Pendulum")
plt.legend()
plt.grid()
plt.show()
```
<a href="https://colab.research.google.com/drive/1Cx_G-OY7GYAVLQc-2ec-hNH3yvQdIdBa?usp=sharing" target="_blank">Colab</a>


## **Conclusion**  

The **forced damped pendulum** is a rich and complex system, revealing fascinating physics principles, from **resonance** to **chaos**. By understanding its behavior through **mathematical models** and **computational simulations**, we gain insight into numerous engineering and natural phenomena.  

Further explorations, such as **nonlinear damping** and **bifurcation studies**, will deepen our understanding of **complex dynamical systems**, bridging theoretical physics and real-world applications.  

