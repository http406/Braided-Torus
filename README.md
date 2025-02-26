# Braided-Torus

### What is a Braided Torus?

A **Braided Torus** is a complex geometric shape that combines the structure of a standard torus (a doughnut-shaped surface) with a "braided" pattern. This braiding effect is achieved by modulating the standard torus equations with additional trigonometric functions, creating a more intricate and visually interesting surface. The braiding introduces a dynamic, woven appearance, giving the torus a sense of movement and depth.

The Braided Torus is often used in mathematical visualization and computer graphics to demonstrate how parametric equations can create complex and aesthetically pleasing shapes.

---

### Explanation of the Equations

The parametric equations for the Braided Torus are as follows:

\[
\begin{cases}
x = r \cos(v) \cos(u) + R \cos(u)(1 + a \cos(nu)) \\
y = 2.5(r \sin(v) + a \sin(nu)) \\
z = r \cos(v) \sin(u) + R \sin(u)(1 + a \cos(nu))
\end{cases}
\]

#### Variables:
- \( R \): The major radius of the torus (distance from the center of the hole to the center of the tube).
- \( r \): The minor radius of the torus (radius of the tube itself).
- \( a \): The modulation factor that controls the amplitude of the braiding effect.
- \( n \): The number of braids (controls how many times the torus is "woven").
- \( u \): The angle parameter for the major circle (ranges from \(-4\pi\) to \(4\pi\)).
- \( v \): The angle parameter for the minor circle (ranges from \(0\) to \(2\pi\)).

#### Components:
1. **Standard Torus**:
   - The standard torus equations are:
     \[
     \begin{cases}
     x = (R + r \cos(v)) \cos(u) \\
     y = r \sin(v) \\
     z = (R + r \cos(v)) \sin(u)
     \end{cases}
     \]
   - These equations describe a circle of radius \( R \) (major radius) with a tube of radius \( r \) (minor radius) wrapped around it.

2. **Braiding Modulation**:
   - The braiding effect is introduced by adding a modulation term \( a \cos(nu) \) to the major radius \( R \). This term varies with the angle \( u \), creating a wavy pattern along the torus.
   - The term \( a \sin(nu) \) is added to the \( y \)-coordinate to create vertical undulations, enhancing the braided appearance.

3. **Scaling**:
   - The \( y \)-coordinate is scaled by a factor of 2.5 to stretch the torus vertically, making the braiding effect more pronounced.

---

### Explanation of the Code

The code provided uses **Three.js** to create and render the Braided Torus in 3D. Here's a detailed breakdown:

#### 1. **Scene Setup**
   - A `THREE.Scene` is created to hold all 3D objects.
   - A `THREE.PerspectiveCamera` is set up to view the scene.
   - A `THREE.WebGLRenderer` is used to render the scene to the browser.

#### 2. **Braided Torus Geometry**
   - The geometry of the Braided Torus is defined using the parametric equations.
   - A nested loop iterates over the parameters \( u \) and \( v \) to calculate the vertices of the torus.
   - The vertices are stored in a `THREE.BufferGeometry` object.

#### 3. **Indices for Faces**
   - Indices are created to define the triangular faces of the torus. Each face is made up of two triangles.

#### 4. **Custom Shader Material**
   - A custom shader material is created using `THREE.ShaderMaterial`.
   - The **vertex shader** passes the vertex positions to the fragment shader.
   - The **fragment shader** applies a gradient color effect based on the vertex positions and time, creating a dynamic color animation.

#### 5. **Space Background with Stars**
   - A star field is created using a `THREE.Points` object.
   - Each star is assigned a random position and color using `THREE.Color` and `setHSL`.
   - The `vertexColors` property of `THREE.PointsMaterial` is enabled to render each star with its assigned color.

#### 6. **Animation Loop**
   - The `animate` function updates the rotation of the torus and the time uniform in the shader, creating a smooth animation.
   - The scene is re-rendered on each frame using `requestAnimationFrame`.

#### 7. **Window Resize Handling**
   - The camera and renderer are updated when the window is resized to maintain the correct aspect ratio.
