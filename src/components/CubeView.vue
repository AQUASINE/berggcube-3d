<template>
<div>
</div>
</template>

<script>
import * as THREE from 'three';

export default {
  name: "CubeView",
  mounted() {
    this.camera = new THREE.PerspectiveCamera(
      75,
      window.innerWidth / window.innerHeight,
      0.1,
      1000
    );
    this.camera.position.z = 2;
    this.renderer = new THREE.WebGLRenderer();
    this.renderer.setSize(window.innerWidth, window.innerHeight);
    this.renderer.setClearColor(0xffffff, 1);
    document.body.appendChild(this.renderer.domElement);
    console.log("CubeView mounted");
    this.cube = new THREE.Mesh(
      new THREE.BoxGeometry(1, 1, 1),
      new THREE.MeshBasicMaterial({ map: new THREE.TextureLoader().load('https://cdn.discordapp.com/emojis/1015738796073025638.webp?size=96&quality=lossless') })
    );
    this.scene = new THREE.Scene();
    this.scene.add(this.cube);

    this.animate();
  },
  methods: {
    animate() {
      requestAnimationFrame(this.animate);
      this.cube.rotation.x += 0.01;
      this.cube.rotation.y += 0.01;
      this.renderer.render(this.scene, this.camera);
    }
  }
}
</script>

<style scoped>

</style>