# Simple JavaScript Graphics scene with WebGL 
 
WebGL enables web content to use an API based on OpenGL ES 2.0 to perform 2D and 3D rendering in an HTML canvas in browsers that support it without the use of plug-ins.
WebGL programs consist of control code written in JavaScript and shader code (GLSL) that is executed on a computer's Graphics Processing Unit (GPU). WebGL elements can be mixed with other HTML elements and composited with other parts of the page or page background.
This project uses WebGL to represent a small interactive graphical scene created as part of a demonstration of WebGL capabilities.

![Demo](https://user-images.githubusercontent.com/55353071/131014346-b4992f77-db05-4bbd-9102-bafb5790a26f.gif)


[![WebGL 2.0](https://img.shields.io/badge/WebGL-2.0-%23FF9900.svg)](https://www.khronos.org/webgl/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)



## 🔥 Features
- **Core WebGL Rendering Pipeline**
- GLSL Shader Integration (Vertex & Fragment)
- Interactive Camera Controls
- Dynamic Buffer Management
- Cross-platform Touch/Desktop Support

## 🚀 Quick Start
```bash
git clone https://github.com/ThanasisTzimourtas/Simple-JavaScript-HTML-Graphic-Scene-with-WebGL.git
cd Simple-JavaScript-HTML-Graphic-Scene-with-WebGL
python -m http.server 8000  # Open browser to localhost:8000
```
🧠 Core Architecture

```bash
WebGL Initialization
// Initialize WebGL context
const gl = canvas.getContext('webgl', {
  antialias: true,
  premultipliedAlpha: false
});

// Create vertex buffer
const vertexBuffer = gl.createBuffer();
gl.bindBuffer(gl.ARRAY_BUFFER, vertexBuffer);
gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(vertices), gl.STATIC_DRAW);
```

Shader Programming (GLSL)

Vertex Shader

```bash
attribute vec3 aPosition;
uniform mat4 uModelViewMatrix;
uniform mat4 uProjectionMatrix;

void main() {
  gl_Position = uProjectionMatrix * uModelViewMatrix * vec4(aPosition, 1.0);
}
```
Fragment Shader
```bash
precision mediump float;
uniform vec3 uColor;

void main() {
  gl_FragColor = vec4(uColor, 1.0);
}
```
Rendering Loop
```bash
function render() {
  gl.clear(gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT);
  
  // Update camera matrices
  const projectionMatrix = mat4.perspective(...);
  const viewMatrix = mat4.lookAt(...);
  
  // Draw geometry
  gl.useProgram(shaderProgram);
  gl.uniformMatrix4fv(uProjectionMatrix, false, projectionMatrix);
  gl.drawArrays(gl.TRIANGLES, 0, vertexCount);
  
  requestAnimationFrame(render);
}
```
## 📦 Key Components  
| Component | Purpose | File |  
|-----------|---------|------|  
| **WebGL Context** | GPU connection & state management | `index.html` |  
| **Shader Loader** | GLSL compilation & linking | `webgl-utils.js` |  
| **Matrix Library** | 3D transformations | `mat4.js` |  
| **Input Handler** | Mouse/touch events | `input.js` |  
| **Render Core** | Main draw cycle logic | `renderer.js` |  

## 🌟 Advanced Techniques  
1. **Double-Buffering**: Minimizes rendering artifacts  
2. **Z-Buffering**: Depth testing via `gl.enable(gl.DEPTH_TEST)`  
3. **Interleaved Vertex Data**: Compact buffer layout  
4. **Shader Hot-Reload**: Dynamic GLSL recompilation  

## 🛠️ Development  
```bash  
npm install                # Install dependencies (gl-matrix)  
npm run dev               # Start dev server with live reload  
npm run build             # Minify JS for production
```
