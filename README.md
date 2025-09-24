# Theory of the Tilt Model and 3D Compass

This document explains the theory behind the **Tilt Model** and how it is applied to a **3D compass** in the context of head direction, tilt, and gravity-based reference systems. We explore how **α (alpha)**, **γ (gamma)**, and their relationships with the gravitational vector \( \mathbf{G} \) map to a unit sphere and how these parameters are used to model head direction and orientation in 3D space.

## 1. Introduction

The **Tilt Model** refers to the orientation of an object (e.g., the head) relative to the gravity vector. By defining this orientation in terms of two parameters, **α (alpha)** and **γ (gamma)**, we can represent the head's position in 3D space and use it as a reference for navigating and determining orientation.

In this model:
- **α (alpha)** is the **tilt angle** with respect to the gravitational vector (range: 0° to 180°).
- **γ (gamma)** is the **tilt direction** or **tilt orientation**, indicating the direction of the tilt (range: -180° to +180°).

This model is particularly useful when developing systems that need to track head orientation, such as for navigation, augmented reality, or for building a 3D compass.

**Interactive Visualization**: For a hands-on demonstration of these concepts, see the [G Vector 3D Visualization](https://pan825.github.io/g.html) which provides an interactive tool to explore tilt angles, gravity vectors, and 3D orientation mapping.

## 2. Tilt Parameters: α (Alpha) and γ (Gamma)

### 2.1. α (Alpha) - Tilt Angle

**α (alpha)** represents the tilt angle between the head's **up axis** and the **gravity vector**  $\mathbf{G} = (G_x, G_y, G_z)$ , where:

- 0° corresponds to the **upright position** (the head is aligned with the gravity vector).
- 180° corresponds to the **inverted position** (the head is upside down relative to gravity).

Mathematically, **α (alpha)** is calculated as the angle between the **head's vertical axis** (up direction) and the **gravity vector**:

$$
\alpha = \arccos(-G_y)
$$

where $G_y$ is the **y-component** of the gravity vector.

### 2.2. γ (Gamma) - Tilt Orientation

**γ (gamma)** is the **tilt direction** or **tilt orientation**, which represents the direction of tilt relative to the head's upright position. It is measured as the azimuth or **horizontal angle** in the **head's horizontal plane**. **γ (gamma)** varies between -180° and +180°, where:

- 0° represents the **nose-down** position (forward).
- +90° represents the **right-ear-down** position.
- -90° represents the **left-ear-down** position.

Mathematically, **γ (gamma)** can be calculated as:

$$
\gamma = \arctan\left(\frac{G_x}{G_z}\right)
$$

where \( G_x \) and \( G_z \) are the **x** and **z-components** of the gravity vector, respectively.

## 3. Mapping α and γ to a Unit Sphere

### 3.1. The Relationship between α, γ, and the Gravity Vector

The **gravity vector** $\mathbf{G} = (G_x, G_y, G_z)$  can be mapped onto a **unit sphere** using the tilt parameters **α (alpha)** and **γ (gamma)**. The conversion from tilt parameters to a 3D vector on the sphere is given by:

$$
G_x = \sin(\alpha) \cdot \sin(\gamma)
$$

$$G_y = -\cos(\alpha)
$$

$$G_z = \sin(\alpha) \cdot \cos(\gamma)
$$

where:
- **α (alpha)** is the tilt angle (from 0° to 180°).
- **γ (gamma)** is the tilt orientation (from -180° to +180°).

The gravity vector \( \mathbf{G} \) represents the "downward" direction relative to the head, with the head's **up axis** corresponding to the **+Y axis** and the **nose-forward axis** corresponding to the **+Z axis**.

### 3.2. From α and γ to the Unit Sphere

Given the equations above, the unit vector **G** can be plotted as a point on a sphere. This is used to track the **head's orientation** in 3D space. The **α (alpha)** and **γ (gamma)** values map directly to coordinates on a sphere, and by modifying these parameters, we can simulate different head orientations and understand their relationship with gravity.

## 4. Mapping α and γ to a 2D Map (Plate Carrée Projection)

To visualize the tilt angles, we can **map** the 3D spherical representation of **α (alpha)** and **γ (gamma)** onto a 2D plane (using a **Plate Carrée projection**).

In this projection:
- **α (alpha)** is mapped to the **vertical axis (y-axis)** of the map, where 0° is at the top (upright) and 180° is at the bottom (inverted).
- **γ (gamma)** is mapped to the **horizontal axis (x-axis)** of the map, where -180° is the left side and +180° is the right side.

The equations for mapping **α** and **γ** to the 2D map coordinates are:


$$x = \frac{\gamma + 180^\circ}{360^\circ} \cdot W$$

$$y = \frac{\alpha}{180^\circ} \cdot H$$


where:
- **W** is the width of the map,
- **H** is the height of the map.

Conversely, we can reverse the mapping from 2D coordinates to **α (alpha)** and **γ (gamma)**:


$$\gamma = \frac{x}{W} \cdot 360^\circ - 180^\circ$$

$$\alpha = \frac{y}{H} \cdot 180^\circ$$


### 4.1. Use of the Map in Navigation and Tilt Detection

This 2D map serves as a simple way to visualize the tilt of an object or head. By mapping the **α (alpha)** and **γ (gamma)** values, we can track the object's orientation in real time, making this model applicable in fields like:
- **Virtual reality**: To simulate head movements and provide realistic navigation.
- **Augmented reality**: To track the real-world orientation of devices and render augmented objects accordingly.
- **Robotics**: For robot navigation and balancing.

## 5. Applications of the Tilt Model

This model is applied in various areas of technology and scientific research:

- **Head Orientation Tracking**: The tilt model is used to monitor and analyze head movements, which can be useful in virtual and augmented reality (VR/AR) systems.
- **Inertial Navigation Systems (INS)**: The model helps track the orientation of vehicles and drones, assisting in navigation and balance.
- **Robotic Systems**: The tilt model can be used to stabilize robotic systems or assist in object manipulation by tracking their orientation.

## 6. Conclusion

The tilt model using **α (alpha)** and **γ (gamma)** provides a powerful and intuitive way to describe an object's orientation in 3D space. By mapping these parameters to a unit sphere or a 2D map, we can visualize and track the object's orientation and movement in real time. This model has wide applications in navigation, virtual and augmented reality, robotics, and more.

---

## References

- **Angelaki, D. E., & Laurens, J. (2020).** A gravity-based three-dimensional compass in the mouse brain. *Nature Communications*.
- **Page, H., et al. (2017).** A detailed model for gravity-based 3D orientation in vertebrates. *Journal of Neurophysiology*.
