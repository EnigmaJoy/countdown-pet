<script setup>
import { ref, onMounted } from 'vue'
import confetti from 'canvas-confetti'

const phase = ref('weeks')
const timeLeft = ref({})
const motivationalQuote = ref('')

const targetDate = new Date('2025-12-31T23:59:59').getTime()

const quotes = [
  "Sei incredibile! ✨",
  "Ogni passo conta! 🚀",
  "Mai smettere di sognare! 🌈",
  "Oggi sarà fantastico! 🧁"
]

onMounted(() => {
  setInterval(updateCountdown, 1000)
  motivationalQuote.value = quotes[Math.floor(Math.random() * quotes.length)]
})

function updateCountdown() {
  const now = new Date().getTime()
  const distance = targetDate - now

  const weeks = Math.floor(distance / (1000 * 60 * 60 * 24 * 7))
  const days = Math.floor(distance / (1000 * 60 * 60 * 24))
  const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
  const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60))
  const seconds = Math.floor((distance % (1000 * 60)) / 1000)

  if (distance <= 0) {
    phase.value = 'celebration'
    confetti()
    return
  }

  if (days <= 3) phase.value = 'hours'
  else if (days <= 7) phase.value = 'days'
  else phase.value = 'weeks'

  timeLeft.value = { weeks, days, hours, minutes, seconds }
}
</script>

<template>
  <div class="text-lg mb-2">
    <template v-if="phase === 'weeks'">
      Mancano {{ timeLeft.weeks }} settimane!
    </template>
    <template v-else-if="phase === 'days'">
      Mancano {{ timeLeft.days }} giorni!
    </template>
    <template v-else-if="phase === 'hours'">
      Mancano {{ timeLeft.hours }}h {{ timeLeft.minutes }}m {{ timeLeft.seconds }}s
    </template>
    <template v-else>
      🎉 È arrivato il momento! 🎉
    </template>
    <div class="text-pink-600 italic mt-2">{{ motivationalQuote }}</div>
  </div>
</template>
