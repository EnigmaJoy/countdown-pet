<script setup>
import { ref } from 'vue'
import anime from 'animejs'

const avatarRef = ref(null)

function animateAvatar() {
  anime({
    targets: avatarRef.value,
    rotateY: [0, 20, -20, 0],
    scale: [1, 1.1, 0.9, 1],
    easing: 'easeInOutSine',
    duration: 800
  })
}

defineExpose({ animateAvatar })
</script>

<template>
  <div ref="avatarRef" class="w-32 h-32 mx-auto mb-4">
    <img src="/src/image/cutie.png" alt="Cute Avatar" class="w-full h-full object-contain" />
  </div>
</template>
