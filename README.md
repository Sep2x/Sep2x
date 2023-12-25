- 👋 Hi, I’m @Sep2x
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Sep2x/Sep2x is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0"
    />
    <title>3D Laboratory Setting</title>
    <style>
      body {
        margin: 0;
      }
    </style>
  </head>
  <body>
    <script type="module">
      import * as THREE from 'https://threejsfundamentals.org/threejs/resources/threejs/r132/build/three.module.js';

      // Create scene
      const scene = new THREE.Scene();

      // Create camera
      const camera = new THREE.PerspectiveCamera(
        75,
        window.innerWidth / window.innerHeight,
        0.1,
        1000
      );
      camera.position.z = 5;

      // Create renderer
      const renderer = new THREE.WebGLRenderer();
      renderer.setSize(window.innerWidth, window.innerHeight);
      document.body.appendChild(renderer.domElement);

      // Create room
      const roomGeometry = new THREE.BoxGeometry(10, 5, 10);
      const roomMaterial = new THREE.MeshBasicMaterial({ color: 0xaaaaaa, side: THREE.BackSide });
      const room = new THREE.Mesh(roomGeometry, roomMaterial);
      scene.add(room);

      // Create equipment (cylinder)
      const cylinderGeometry = new THREE.CylinderGeometry(1, 1, 3, 32);
      const cylinderMaterial = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
      const cylinder = new THREE.Mesh(cylinderGeometry, cylinderMaterial);
      scene.add(cylinder);

      // Set cylinder dimensions
      const diameter = 2; // Diameter of the cylinder
      const length = 4;   // Length of the cylinder
      cylinder.scale.set(diameter / 2, length / 2, diameter / 2);

      // Animation loop
      function animate() {
        requestAnimationFrame(animate);

        // Rotate the cylinder
        cylinder.rotation.x += 0.01;
        cylinder.rotation.y += 0.01;

        renderer.render(scene, camera);
      }

      // Handle window resize
      window.addEventListener('resize', () => {
        const newWidth = window.innerWidth;
        const newHeight = window.innerHeight;

        camera.aspect = newWidth / newHeight;
        camera.updateProjectionMatrix();

        renderer.setSize(newWidth, newHeight);
      });

      animate();
    </script>
  </body>
</html>
