
# Guide to Recursive Inscriptions on Dogecoin

This guide provides instructions on how to create recursive inscriptions using the Dogecoin blockchain, enabling the creation of interconnected digital assets with JavaScript, HTML, and 3D models.

## Overview

Recursive inscriptions involve creating a "parent" inscription that other "child" inscriptions refer back to, forming a network of linked digital assets on the blockchain.

## Step 1: Create the Parent Inscription

The parent inscription acts as the foundational asset. It can be a JavaScript script, a 3D model in GLTF format, HTML content, or other digital media.

### Example: Parent JS Inscription

Here is an example of the Nerd Stones 3D scene using three.js:

https://dogecdn.ordinalswallet.com/inscription/content/da759d4d72fbdefb9d0d81c41e2c7a90bca7c9b6b5f0be8d5cba3a9f310dd0bai0

Assets referenced should be suitable for blockchain referencing, with URL paths adjusted for recursive access:

```javascript
const materials = [
  new THREE.MeshPhongMaterial({ map: loader.load('/content/53ed29d8...') }),
  ...
];
```

### Additional Example: 3D Model Inscription for DPAY Stones

HTML content designed to display a 3D model using three.js and the GLTFLoader:

```
<html lang="en">
  <head>
    <meta charset="utf-8">
    <script type="module" src="/content/c3b478dc1b3a0fa789c65e53aebaa47bd6917a0d17384891bd694c42b1036133i0"></script>
    <style>
      model-viewer {
        position: fixed;
        width: 100%;
        height: 100%;
      }
    </style>
  </head>
  <body>
      <model-viewer src="/content/1101c9b8c3219c40ba5b63a04e4246aa0ef31457aeda689f11fc0478ece4c049i0" camera-controls="" touch-action="pan-y" auto-rotate="" ar-status="not-presenting" style="width: 100%; height: 100%;"></model-viewer>
  </body>
</html>
```

## Step 2: Inscribe the Parent Inscription

Convert the content into a format suitable for inscription on the Dogecoin blockchain, ensuring that the script and model paths reference content stored on the blockchain.

## Step 3: Create Child Inscriptions

Create child inscriptions that reference the parent, which could be other scripts, media files, or derivative works.

### Example: Child HTML Inscription

Example child for nerd stones

```<html>
<head>
    <title>Nerd Stone #396</title>
    <script src="/content/f8d6d9594ff93cb4190cfa81d877b81b59b0d2acd975685fdd12efd0452bd190i0"></script>
</head>
<body>
    <script src="/content/da759d4d72fbdefb9d0d81c41e2c7a90bca7c9b6b5f0be8d5cba3a9f310dd0bai0"></script>
</body>
</html>
```

Example child for dpay stones

```html

<html lang="en">
  <head>
    <meta charset="utf-8">
    <script type="module" src="/content/c3b478dc1b3a0fa789c65e53aebaa47bd6917a0d17384891bd694c42b1036133i0"></script>
    <style>
      model-viewer {
        position: fixed;
        width: 100%;
        height: 100%;
      }
    </style>
  </head>
  <body>
      <model-viewer src="/content/1101c9b8c3219c40ba5b63a04e4246aa0ef31457aeda689f11fc0478ece4c049i0" camera-controls="" touch-action="pan-y" auto-rotate="" ar-status="not-presenting" style="width: 100%; height: 100%;"></model-viewer>
  </body>
</html>
```

## Step 4: Inscribe the Child Inscriptions

Ensure each child inscription effectively links back to its parent or other inscriptions to maintain the recursive structure.

## Step 5: Verify and Utilize Inscriptions

Ensure all inscriptions are correctly linked and retrievable from the blockchain. Develop interfaces for interacting with these inscriptions that are intuitive and functional.

By integrating JavaScript libraries and 3D models into HTML content and inscribing them onto the Dogecoin blockchain, you create a rich ecosystem of interactive and interconnected digital assets. This enhances the user experience and adds value through the recursive nature of linked digital assets.

# Testing and Preparing Scripts for Inscription on Dogecoin

This is a guide on how to use HTTP links to test and prepare HTML and JavaScript scripts before inscribing them onto the Dogecoin blockchain. This method ensures that your scripts function correctly in a web environment similar to their final deployment.

## Overview

Using absolute HTTP links to test your scripts allows you to validate functionality directly from an external server, simulating real-world usage before blockchain inscription.

## Step 1: Create Your HTML File

Create an HTML file that includes external scripts via HTTP links. Here's an example of how to structure your HTML:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Nerd Stone #10000</title>
    <script src="https://dogecdn.ordinalswallet.com/inscription/content/f8d6d9594ff93cb4190cfa81d877b81b59b0d2acd975685fdd12efd0452bd190i0"></script>
</head>
<body>
    <script src="script.js"></script>
</body>
</html>
```

## Step 2: Test the HTML File

- **Open the HTML file in a web browser**: Simply drag and drop the file into a browser or open it through the browser's file menu.
- **Use browser developer tools**: Access tools like Chrome DevTools to inspect network activity, view console logs, and debug scripts.

## Step 3: Adjust for Local Testing If Needed

For rapid testing and iteration, you might want to use local copies of the scripts. Adjust the `<script>` tag to point to local versions during development:

```html
<script src="local/path/to/script.js"></script>
```

## Step 4: Prepare Scripts for Inscription

Once testing is complete, prepare your scripts for inscription:
- **Remove the domain prefix**: Modify the script paths to use paths suitable for the blockchain environment.

Example change:
```html
<script src="https://dogecdn.ordinalswallet.com/inscription/content/f8d6d9594ff93cb4190cfa81d877b81b59b0d2acd975685fdd12efd0452bd190i0"></script>
```
To:
```html
<script src="/content/f8d6d9594ff93cb4190cfa81d877b81b59b0d2acd975685fdd12efd0452bd190i0"></script>
```

## Step 5: Inscribe on Dogecoin Blockchain

With your scripts tested and adjusted, proceed with the inscription process on the Dogecoin blockchain.

## More Examples

Nerd Stone test parent

```
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

const loader = new THREE.TextureLoader();
const materials = [
new THREE.MeshPhongMaterial({ map: loader.load('https://dogecdn.ordinalswallet.com/inscription/content/53ed29d8c6b06e6e54d4db2d3e577bbf69354969f9aaa6f2af655ce52fd9c77ai0') }), // right side
new THREE.MeshPhongMaterial({ map: loader.load('https://dogecdn.ordinalswallet.com/inscription/content/53ed29d8c6b06e6e54d4db2d3e577bbf69354969f9aaa6f2af655ce52fd9c77ai0') }), // left side
new THREE.MeshPhongMaterial({ map: loader.load('https://dogecdn.ordinalswallet.com/inscription/content/53ed29d8c6b06e6e54d4db2d3e577bbf69354969f9aaa6f2af655ce52fd9c77ai0') }), // top side
new THREE.MeshPhongMaterial({ map: loader.load('https://dogecdn.ordinalswallet.com/inscription/content/53ed29d8c6b06e6e54d4db2d3e577bbf69354969f9aaa6f2af655ce52fd9c77ai0') }), // bottom side
new THREE.MeshPhongMaterial({ map: loader.load('https://dogecdn.ordinalswallet.com/inscription/content/53ed29d8c6b06e6e54d4db2d3e577bbf69354969f9aaa6f2af655ce52fd9c77ai0') }), // front side
new THREE.MeshPhongMaterial({ map: loader.load('https://dogecdn.ordinalswallet.com/inscription/content/9e542edf2b114b0ff653aff36bc9b929c8dea0813c95191d86e821d0f7441b4fi0') })  // back side
];

// add light
const light = new THREE.DirectionalLight(0xffffff, 1);
light.position.set(0, 1, 1).normalize();
scene.add(light);


// Function to add multiple point lights
function addPointLights(baseIntensity, spacing, numLights, yPosition) {
    for (let i = -numLights / 2; i <= numLights / 2; i++) {
      for (let j = -numLights / 2; j <= numLights / 2; j++) {
        const pointLight = new THREE.PointLight(0xe10202, baseIntensity, 50);
        pointLight.position.set(i * spacing, yPosition, j * spacing);
        scene.add(pointLight);
      }
    }
  }
  
  // Adding lights in a grid
  addPointLights(0.5, 2, 5, -5); // Adjust spacing and intensity as needed
  

// Create a cube
const geometry = new THREE.BoxGeometry();
const cube = new THREE.Mesh(geometry, materials);
scene.add(cube);

// Set initial scale and rotation of the cube
cube.scale.set(3, 3, 3);


// Adjust the camera's position
camera.position.set(0, 3, 10); // Move the camera to a higher y position and slightly back on the z-axis

// Tilt the camera to look at the cube
camera.lookAt(scene.position);

let isDragging = false;
let previousMousePosition = {
    x: 0,
    y: 0
};

renderer.domElement.addEventListener('mousedown', e => {
    isDragging = true;
});

renderer.domElement.addEventListener('mousemove', e => {
    if (isDragging) {
        const deltaMove = {
            x: e.offsetX - previousMousePosition.x,
            y: e.offsetY - previousMousePosition.y
        };

        const rotationSpeed = 0.005;

        cube.rotation.y += deltaMove.x * rotationSpeed;
        cube.rotation.x += deltaMove.y * rotationSpeed;
    }

    previousMousePosition = {
        x: e.offsetX,
        y: e.offsetY
    };
});

renderer.domElement.addEventListener('mouseup', e => {
    isDragging = false;
});

window.addEventListener('resize', () => {
    const width = window.innerWidth;
    const height = window.innerHeight;
    renderer.setSize(width, height);
    camera.aspect = width / height;
    camera.updateProjectionMatrix();
});

function animate() {
    requestAnimationFrame(animate);
    renderer.render(scene, camera);
}

animate();
```

Nerd Stone Test child
```
<!DOCTYPE html>
<html>
<head>
    <title>Nerd Stone #10000</title>
    <script src="https://dogecdn.ordinalswallet.com/inscription/content/f8d6d9594ff93cb4190cfa81d877b81b59b0d2acd975685fdd12efd0452bd190i0"></script>
</head>
<body>
    <script src="script.js"></script>
</body>
</html>
```

This guide helps you ensure that your digital assets function correctly before committing them to the blockchain, using a practical and efficient testing method.
