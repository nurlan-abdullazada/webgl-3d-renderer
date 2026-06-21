# 3D WebGL Renderer

A real-time **3D renderer** built from scratch with the raw **WebGL** API and **JavaScript**. It draws textured 3D cubes with custom GLSL shaders, basic directional lighting, and an interactive camera you can orbit and move through. Matrix math is handled with `gl-matrix`. Built as a Computer Graphics course project.

---

## Features

- **Raw WebGL pipeline** — buffers, attributes, and draw calls written directly against the WebGL API (no rendering framework).
- **Custom GLSL shaders** — hand-written vertex and fragment shaders compiled at runtime, with the standard `Projection × View × Model` transform.
- **Texture mapping** — UV-mapped wood texture applied to cube faces via `texture2D`.
- **Directional lighting** — a simple sun-light model (direction, color, ambient term) modulating texel color.
- **Multiple objects** — several cubes rendered with independent model matrices.
- **Interactive camera** — perspective projection with mouse-look (yaw/pitch) and keyboard navigation, plus depth testing for correct occlusion.

---

## Controls

| Input | Action |
|-------|--------|
| **Ctrl + mouse** | Rotate the camera (look around) |
| **Arrow keys** | Move the camera |

---

## How It Works

1. A unit cube is defined as interleaved vertex data (`X, Y, Z, U, V`) with an index buffer.
2. Vertex and fragment shaders are compiled and linked into a shader program; vertex position, texture coordinate, and normal attributes are bound.
3. The wood texture is uploaded to the GPU and sampled in the fragment shader; a directional light scales the sampled color.
4. The `Camera` class builds the perspective projection and updates the view matrix from mouse and keyboard input each frame.
5. The render loop sets the projection/view/model matrices as uniforms and issues `drawElements` calls for each cube with depth testing enabled.

---

## Project Structure

```
.
├── index.html               # Canvas + script includes
├── index.js                 # WebGL setup, shaders, geometry, render loop
├── camera.js                # Camera class: projection, mouse-look, keyboard movement
├── gl-matrix.js             # Matrix/vector math library
├── index.css                # Page styling
├── qubodup-light_wood.png   # Cube texture
└── Project Documentation.docx
```

---

## Getting Started

A static site — no build step or dependencies.

```bash
git clone https://github.com/nurlan-abdullazada/Computer_Graphics.git
cd Computer_Graphics

# serve locally (a local server avoids texture CORS issues)
python -m http.server 8000
# then open http://localhost:8000
```

Use **Ctrl + mouse** to look around and the **arrow keys** to move.

---

## Team & Contributions

This was a collaborative course project:

- **Nurlan Abdullazada** — WebGL/shader setup and geometry (`index.js` through the vertex-attribute association).
- **Fardi Abdullazade** — rendering code following the vertex-attribute association.
- **Kamran Khanmammadov** — the camera system (`camera.js`).

---

## Author (repository)

[Nurlan Abdullazada](https://github.com/nurlan-abdullazada)
