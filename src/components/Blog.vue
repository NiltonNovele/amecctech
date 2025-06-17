<template>
  <div class="min-h-screen py-12 px-4 sm:px-8 relative overflow-hidden">
    <!-- Confetti canvas -->
    <canvas ref="confettiCanvas" class="absolute inset-0 pointer-events-none z-10"></canvas>

    <h1 class="text-4xl font-extrabold text-center mb-12 relative z-20 text-gray-900 dark:text-white">
      Awards & Recognition
    </h1>

    <div class="grid gap-10 md:grid-cols-3 max-w-6xl mx-auto relative z-20">
      <!-- 2nd Place -->
      <div class="bg-gray-100 dark:bg-zinc-900 rounded-2xl p-8 text-center border border-gray-300 dark:border-zinc-700 shadow-sm hover:shadow-md transition">
        <div class="text-6xl text-gray-400 mb-4">🥈</div>
        <h2 class="text-xl font-semibold text-blue-500 mb-3">2nd PLACE</h2>
        <p class="text-yellow-500 text-3xl font-bold mb-5">R 500</p>
        <ul class="text-gray-700 dark:text-gray-300 space-y-3 text-sm">
          <li><strong>Job Shadowing</strong> (Experience daily business operations)</li>
          <li>Participation Certificate</li>
          <li>Participation Gifts</li>
        </ul>
      </div>

      <!-- 1st Place - Highlighted -->
      <div class="bg-yellow-400 text-black rounded-3xl p-10 text-center shadow-2xl transform scale-105 border-4 border-yellow-300 hover:scale-110 transition-transform duration-300">
        <div class="text-7xl mb-3">🥇</div>
        <h2 class="text-3xl font-bold mb-3">1st PLACE</h2>
        <p class="text-4xl font-extrabold mb-6">R 1200</p>
        <ul class="text-md space-y-4 font-semibold">
          <li><strong>Professional Internship</strong> (Three-month duration)</li>
          <li><strong>Active Participation in Solution Development</strong> (With mentoring & guidance throughout)</li>
          <li>Certificate and Participation Gifts</li>
        </ul>
      </div>

      <!-- 3rd Place -->
      <div class="bg-gray-100 dark:bg-zinc-900 rounded-2xl p-8 text-center border border-gray-300 dark:border-zinc-700 shadow-sm hover:shadow-md transition">
        <div class="text-6xl text-gray-400 mb-4">🥉</div>
        <h2 class="text-xl font-semibold text-blue-500 mb-3">3rd PLACE</h2>
        <p class="text-yellow-500 text-3xl font-bold mb-5">R 250</p>
        <ul class="text-gray-700 dark:text-gray-300 space-y-3 text-sm">
          <li><strong>Technical Courses</strong> (On online learning platforms)</li>
          <li>Participation Certificate</li>
          <li>Participation Gifts</li>
        </ul>
      </div>
    </div>

    <div class="max-w-3xl mx-auto mt-20 text-center leading-relaxed relative z-20 text-gray-700 dark:text-gray-300">
      <p class="mb-6 text-lg font-medium">
        More than winning, this event celebrates collaboration, creativity, and the courage to share ideas with the world.
      </p>
      <p class="text-md">
        Regardless of placement, every participant takes away new connections, valuable learning, and the experience of building something meaningful.
      </p>
    </div>
  </div>
</template>


<script setup>
import { onMounted, ref } from 'vue'
import confetti from 'canvas-confetti'

const confettiCanvas = ref(null)

onMounted(() => {
  const myConfetti = confetti.create(confettiCanvas.value, {
    resize: true,
    useWorker: true,
  })

  // Function to generate random positions across the screen
  const shoot = () => {
    myConfetti({
      particleCount: 5,
      angle: 90,
      spread: 360,
      origin: {
        x: Math.random(),
        y: 0
      }
    })
  }

  // Start confetti rain
  const interval = setInterval(shoot, 100)

  // Stop after 5 seconds
  setTimeout(() => {
    clearInterval(interval)
  }, 5000)
})
</script>

