<script setup>
import Avatar from '../components/Avatar.vue'
import Countdown from '../components/Countdown.vue'
import InteractionButtons from '../components/InteractionButtons.vue'

const avatarRef = ref(null)

function petAvatar() {
  avatarRef.value.animateAvatar()
}
</script>

<template>
  <div class="min-h-screen flex flex-col items-center justify-center bg-yellow-100 p-4 text-center">
    <div class="w-full max-w-md p-6 bg-white rounded-2xl shadow-lg">
      <Avatar ref="avatarRef" />
      <h1 class="text-2xl font-bold mb-2">Il tuo conto alla rovescia!</h1>
      <Countdown />
    </div>
    <InteractionButtons @petAvatar="petAvatar" />
  </div>
</template>
