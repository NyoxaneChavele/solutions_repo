# Problem 1
# Orbital Period and Orbital Radius

## 1. Introduction
Celestial mechanics, the study of planetary motions and gravitational interactions, has been guided for centuries by Johannes Kepler’s laws. One of the most profound of these is **Kepler’s Third Law**, which states that the square of a planet’s orbital period is proportional to the cube of its orbital radius. This principle is instrumental in understanding planetary orbits, satellite trajectories, and even interstellar navigation.

In this report, we will derive the mathematical relationship governing orbital motion, explore its implications in astronomy, analyze real-world examples, and implement a computational model to verify our findings.

## 2. Derivation of Kepler’s Third Law
### 2.1 Newton’s Laws and Centripetal Force
For a planet or satellite in a stable circular orbit around a central mass \( M \), the gravitational force acts as the necessary centripetal force:

\[ F_g = F_c \]

Using Newton’s Law of Universal Gravitation:

\[ F_g = \frac{GMm}{r^2} \]

And the equation for centripetal force:

\[ F_c = \frac{mv^2}{r} \]

Setting these equal to each other:

\[ \frac{GMm}{r^2} = \frac{mv^2}{r} \]

Canceling \( m \) and solving for velocity:

\[ v^2 = \frac{GM}{r} \]

Since orbital velocity is related to the orbital period \( T \) by:

\[ v = \frac{2\pi r}{T} \]

Substituting this into the velocity equation:

\[ \left( \frac{2\pi r}{T} \right)^2 = \frac{GM}{r} \]

Rearranging:

\[ T^2 = \frac{4\pi^2}{GM} r^3 \]

This is Kepler’s Third Law, demonstrating that the square of the orbital period \( T^2 \) is proportional to the cube of the orbital radius \( r^3 \).

## 3. Implications in Astronomy
### 3.1 Determining Planetary Masses
By measuring the orbital period and radius of a satellite, astronomers can deduce the mass of the central body. For instance, applying Kepler’s Third Law to Jupiter’s moons helps estimate Jupiter’s mass.

### 3.2 Calculating Planetary Distances
Kepler’s law allows astronomers to determine distances in the solar system. By comparing the periods and radii of planetary orbits, they can measure astronomical units (AU) without direct observation.

### 3.3 Satellite Orbits and Space Missions
Satellite engineers use Kepler’s Law to design stable orbits for communication and research satellites. The **Geostationary Orbit (GEO)** is determined based on this principle, ensuring satellites maintain a fixed position relative to Earth.

## 4. Real-World Examples
### 4.1 The Moon’s Orbit Around Earth
The Moon’s period (\( T \)) is approximately **27.3 days**, and its average orbital radius (\( r \)) is **384,400 km**. Using Kepler’s formula, we can estimate the Earth’s mass.

### 4.2 The Planets in the Solar System
For each planet, the relationship \( T^2 \propto r^3 \) holds, as seen in the table below:

| Planet  | Orbital Radius (AU) | Orbital Period (Years) | \( T^2 / r^3 \)  |
|---------|---------------------|------------------------|-----------------|
| Mercury | 0.39                | 0.24                   | ~1.0            |
| Venus   | 0.72                | 0.62                   | ~1.0            |
| Earth   | 1.00                | 1.00                   | ~1.0            |
| Mars    | 1.52                | 1.88                   | ~1.0            |
| Jupiter | 5.20                | 11.86                  | ~1.0            |

This confirms the universal validity of Kepler’s law.

## 5. Computational Simulation
To visualize this relationship, we implement a Python simulation using **Matplotlib** and **NumPy**. The program calculates and plots the orbit of a body based on initial conditions.
![alt text][def]
<a href="https://colab.research.google.com/drive/1yb2VWrmBY-BJRZOSQ39ojd1j9c9MpJkr?usp=sharing" target="_blank">Colab</a>

This graph confirms the linear relationship between \( T^2 \) and \( r^3 \), validating Kepler’s law computationally.

## 6. Extension to Elliptical Orbits
While Kepler’s law is derived for circular orbits, it extends to elliptical orbits by considering the **semi-major axis** \( a \) instead of \( r \):

\[ T^2 = \frac{4\pi^2}{GM} a^3 \]

This applies to:
- **Cometary orbits**, where highly elliptical paths still obey Kepler’s Third Law.
- **Exoplanet detection**, where variations in a star’s brightness hint at planetary orbits.

## 7. Conclusion
Kepler’s Third Law elegantly bridges classical mechanics with real-world astronomy. By deriving and computationally verifying \( T^2 \propto r^3 \), we reinforce its fundamental role in celestial mechanics. Applications range from planetary science to space exploration, making it an essential tool for astronomers and engineers alike. Future work could involve incorporating **gravitational perturbations** and **relativistic effects** for even greater accuracy.

**Keywords:** Kepler’s Third Law, Orbital Mechanics, Celestial Motion, Computational Simulation, Astronomy.



[def]: image.png