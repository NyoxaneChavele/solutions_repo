# Problem 1
import numpy as np
import matplotlib.pyplot as plt
import io
import base64

# ## Projectile Motion Analysis

# This script computes and visualizes the range, maximum height, and time of flight of a projectile based on its launch angle.

# ### Importing Required Libraries

# We use NumPy for calculations and Matplotlib for plotting.

# ### Function to Compute Projectile Motion Parameters
def projectile_motion(theta, v0, g=9.81):
    """Computes the range, max height, and time of flight of a projectile given launch angle theta (degrees), 
    initial velocity v0, and gravity g."""
    theta_rad = np.radians(theta)  # Convert angle to radians
    range_ = (v0**2 * np.sin(2 * theta_rad)) / g
    max_height = (v0**2 * (np.sin(theta_rad))**2) / (2 * g)
    time_of_flight = (2 * v0 * np.sin(theta_rad)) / g
    return range_, max_height, time_of_flight

# ### Defining Parameters
v0 = 20  # Initial velocity in m/s
theta_values = np.linspace(0, 90, 100)  # Angles from 0 to 90 degrees
ranges, heights, times = zip(*[projectile_motion(theta, v0) for theta in theta_values])

# ### Generating the Plot
def generate_plot():
    fig, ax = plt.subplots()
    ax.plot(theta_values, ranges, label='Range (m)', color='b')
    ax.plot(theta_values, heights, label='Max Height (m)', color='r')
    ax.plot(theta_values, times, label='Time of Flight (s)', color='g')
    ax.set_xlabel('Angle of Projection (degrees)')
    ax.set_ylabel('Values')
    ax.set_title('Projectile Motion Analysis')
    ax.legend()
    ax.grid()
    
    img = io.BytesIO()
    plt.savefig(img, format='png')
    img.seek(0)
    plt.close(fig)
    return base64.b64encode(img.getvalue()).decode()

# ### Output Results
def generate_report():
    """Generates a Markdown report with results and a base64-encoded plot."""
    plot_data = generate_plot()
    report = f"""
# Projectile Motion Analysis

This report analyzes the projectile motion based on different launch angles. The results include:

- **Range**: Distance traveled before hitting the ground.
- **Maximum Height**: The highest point reached by the projectile.
- **Time of Flight**: The total duration before landing.

## Computed Data:

| Angle (degrees) | Range (m) | Max Height (m) | Time of Flight (s) |
|----------------|----------|---------------|------------------|
"""
    for theta, r, h, t in zip(theta_values, ranges, heights, times):
        report += f"| {theta:.1f} | {r:.2f} | {h:.2f} | {t:.2f} |
"
    report += """

## Visualization:

![Projectile Motion Plot](data:image/png;base64,{plot_data})
    """
    return report

if __name__ == '__main__':
    with open("projectile_motion_report.md", "w") as f:
        f.write(generate_report())
    print("Report saved as projectile_motion_report.md")
