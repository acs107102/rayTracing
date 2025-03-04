# RayTracer: A Photorealistic Ray Tracing Renderer

## Introduction
This project is an advanced ray tracer developed as part of the Computer Graphics course (Spring 2023). It follows a structured implementation of ray tracing, supporting Blinn-Phong shading, reflections, refractions, texture mapping, bounding volume hierarchies (BVH), and distributed ray tracing. The goal is to create photorealistic renderings while optimizing performance.

This implementation is inspired by **Ray Tracing in One Weekend**, Scratchapixel, YouTube tutorials, and various GitHub projects. Below is a structured workflow for the development process.

## Features Implemented

### Basic Ray Tracing
- **Pinhole Camera**: Implements a simple pinhole camera model for rendering.
- **Point Light Source**: Enables basic illumination.
- **Ray-Shape Intersections**:
  - Sphere: Implements ray-sphere intersection using quadratic solutions.
  - Planar Quad: Computes intersection using normal vectors and plane equations.
  - Triangle: Uses barycentric coordinates to determine if a ray hits the triangle.
  - Triangle Meshes: Reads and processes PLY files to form complex objects.
- **Blinn-Phong Shading**: A fundamental shading model for realistic rendering.

### Advanced Features
- **Texture Mapping**:
  - Sphere, Planar Quad, Triangle, Triangle Meshes
  - Implements UV coordinate transformations
- **Reflection and Refraction**: Supports mirror-like reflections and glass-like materials using secondary rays.
- **Bounding Volume Hierarchy (BVH)** (In progress): Accelerates ray-object intersections for improved performance.
- **Distributed Ray Tracing**:
  - Depth of Field (Thin Lens Camera Model)
  - Soft Shadows (Area Light Source)
  - Random vs. Jittered Sampling Comparison
- **Custom Scene**: A showcase of implemented features with complex object arrangements.

## Implementation Details
### 1. Workflow
The ray tracing process follows these steps:
1. **Scene Parsing**: Reads scene data from JSON input files, extracting objects, lights, and camera properties.
2. **Ray Generation**: Computes primary rays from the camera.
3. **Intersection Testing**: Uses mathematical formulations for ray-object intersections.
4. **Shading & Lighting**: Implements Blinn-Phong shading using diffuse and specular components.
5. **Recursive Ray Tracing**: Handles reflections and refractions based on material properties.
6. **Texture Mapping**: Maps 2D textures onto 3D objects using calculated UV coordinates.
7. **Optimization**: Implements basic acceleration structures and prepares for BVH integration.
8. **Rendering & Output**: Generates a final `.ppm` image output.

### 2. UML Class Structure
This project follows an object-oriented approach, structured according to the provided UML diagram. Key classes include:
- `RayTracer`: Core engine handling scene setup and rendering.
- `Camera`: Base class for Pinhole and Thin Lens cameras.
- `LightSource`: Defines point and area light sources.
- `Shape`: Abstract base class for all geometric primitives.
- `TriangleMesh`: Reads and processes PLY files.
- `BVH` (Planned): Implements a bounding volume hierarchy for efficient intersection testing.

## Usage Instructions
### 1. Build and Run
Ensure you have `CMake` installed, then execute the following commands:
```sh
cd /path/to/RayTracer
mkdir build && cd build
cmake ..
make
./raytracer <input.json>
```
### 2. Example Usage
```sh
./raytracer scenes/sample_scene.json
```
The output will be saved as a `.ppm` image file.

## Results & Performance
- The final rendered image showcases various features such as reflections, refractions, soft shadows, and texture mapping.
- Performance comparison with and without BVH demonstrates significant speedup in rendering.
- Jittered sampling reduces noise in distributed ray tracing compared to random sampling.

### Sample Rendered Images
#### 1. Ray-Sphere Intersection
- Implemented using quadratic solutions to determine intersections.
- **Issue Fixed**: Initial color inaccuracies corrected by refining shading calculations.

#### 2. Ray-Plane Intersection
- Plane normal computed using cross products of edges.
- **Issue Fixed**: Adjusted intersection logic to prevent incorrect rendering artifacts.

#### 3. Ray-Triangle Intersection
- Uses barycentric coordinate method for robust intersection testing.
- **Reference**: Scratchapixel’s geometric solution.

#### 4. Ray-Mesh Intersection
- PLY file reader implemented to parse vertex and face data.
- **Issue Fixed**: Triangle-based intersection improved for complex mesh rendering.

#### 5. Blinn-Phong Shading & Reflection
- Diffuse and specular reflection calculated using normal vectors and light direction.
- **Issue Fixed**: Reflection rendering corrected to properly handle multiple objects.

#### 6. Texture Mapping
- UV mapping applied to sphere, plane, and triangle meshes.
- **Issue Fixed**: Adjusted texture scaling for better alignment.

## Future Enhancements
- Implementing **Bounding Volume Hierarchy (BVH)** for optimized rendering.
- Expanding **path tracing** capabilities for improved global illumination.
- Supporting additional materials like **subsurface scattering**.
- Refining **texture mapping for complex meshes** to improve accuracy.

## Acknowledgments
This project was developed as part of the Computer Graphics course at University of Edinburgh. The provided base code and libraries were instrumental in structuring the implementation. Inspiration was drawn from **Ray Tracing in One Weekend**, **Scratchapixel**, and **various GitHub projects**.

## References
- [PBRT: Physically Based Rendering](https://pbrt.org/)
- [Ray Tracing in One Weekend](https://raytracing.github.io/)
- [Scratchapixel - Ray Tracing Tutorials](https://www.scratchapixel.com/)
- Course Material: [Computer Graphics Spring 2023]
