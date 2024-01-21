<script setup lang="ts">
import { onMounted, ref } from 'vue'
import * as THREE from 'three'

const canvas = ref<HTMLCanvasElement | null>(null)
// Scene
const scene = new THREE.Scene()
const axesHelper = new THREE.AxesHelper(5)
scene.add(axesHelper)

// Object
const geometry = new THREE.BoxGeometry(1, 1, 1)
const material = new THREE.MeshBasicMaterial({ color: 'orange', wireframe: true })
const mesh = new THREE.Mesh(geometry, material)

scene.add(mesh)

// Camera
const sizes = {
  width: 800,
  height: 800
}

const camera = new THREE.PerspectiveCamera(75, sizes.width / sizes.height)
camera.position.z = 3
camera.position.y = 1

scene.add(camera)

let renderer: WebGLRenderer
const clock = new THREE.Clock()

const tick = () => {
  const ellapsedTime = clock.getElapsedTime()

  // mesh.rotation.y = ellapsedTime
  mesh.position.x = Math.cos(ellapsedTime)
  mesh.position.y = Math.sin(ellapsedTime)

  camera.lookAt(mesh.position)

  renderer.render(scene, camera)
  window.requestAnimationFrame(tick)
}

onMounted(() => {
  renderer = new THREE.WebGLRenderer({
    canvas: canvas.value
  })

  renderer.setSize(sizes.width, sizes.height)

  tick()
})
</script>

<template>
  <div>
    <canvas ref="canvas"></canvas>
  </div>
</template>
