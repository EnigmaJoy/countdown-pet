<script setup>
const emit = defineEmits(['petAvatar'])
</script>

<template>
  <div class="mt-6 flex gap-4 justify-center">
    <button @click="$emit('petAvatar')" class="px-4 py-2 rounded-xl bg-pink-400 text-white font-bold shadow hover:scale-105 transition">
      Accarezza 💖
    </button>
    <button @click="() => alert('🍰 *avatar mangia felice*')" class="px-4 py-2 rounded-xl bg-green-400 text-white font-bold shadow hover:scale-105 transition">
      Dai da mangiare 🍰
    </button>
  </div>
</template>
