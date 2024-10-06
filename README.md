# Spinning Cube Visualization

This project is a fun ASCII visualization of a spinning cube, created using C and basic 3D math for rotational transformations. The cube spins and projects itself into 2D ASCII art, simulating depth and perspective.

[Watch the Demo Video on YouTube](https://www.youtube.com/watch?v=V84OzhN--y4)

## How It Works

The spinning cube is rendered using trigonometric functions to rotate a 3D object in space. The rotation is calculated around three axes (x, y, z) with three angles: `A`, `B`, and `C`, which are updated continuously to achieve the spinning effect. 

### Math behind the Rotations

The 3D position of a point on the cube is determined by its coordinates (i, j, k). These coordinates are transformed into new coordinates (x, y, z) through the following formulas:

- **X-axis Rotation:**
    \[
    x = j \cdot \sin(A) \cdot \sin(B) \cdot \cos(C) - k \cdot \cos(A) \cdot \sin(B) \cdot \cos(C) + j \cdot \cos(A) \cdot \sin(C) + k \cdot \sin(A) \cdot \sin(C) + i \cdot \cos(B) \cdot \cos(C)
    \]

- **Y-axis Rotation:**
    \[
    y = j \cdot \cos(A) \cdot \cos(C) + k \cdot \sin(A) \cdot \cos(C) - j \cdot \sin(A) \cdot \sin(B) \cdot \sin(C) + k \cdot \cos(A) \cdot \sin(B) \cdot \sin(C) - i \cdot \cos(B) \cdot \sin(C)
    \]

- **Z-axis Rotation:**
    \[
    z = k \cdot \cos(A) \cdot \cos(B) - j \cdot \sin(A) \cdot \cos(B) + i \cdot \sin(B)
    \]

These transformed coordinates are then projected into a 2D plane by calculating the screen position of each point on the cube based on its z-depth.

## Libraries Used

- **math.h**: For trigonometric functions such as `sin()` and `cos()` which are essential for calculating the rotations in 3D space.
- **stdio.h**: Used for outputting the ASCII cube onto the terminal.
- **unistd.h / windows.h**: To create a short delay between frames (`usleep()` on Unix systems or `WaitableTimer()` on Windows) to animate the cube smoothly.

## Features

- **ASCII Art Rendering**: The cube is rendered as ASCII characters with different characters representing different cube faces (e.g., `☻`, `$`, `~`).
- **3D Depth Simulation**: The project uses a simple depth buffer (z-buffer) to simulate which parts of the cube should appear in front of or behind other parts.
- **Dynamic Resizing**: The code renders cubes of different sizes within the same frame, creating the illusion of depth with multiple cubes.

## How to Run

To run the project, simply compile it using a C compiler. For example:

```bash
gcc spinning_cube.c -o spinning_cube -lm
./spinning_cube
