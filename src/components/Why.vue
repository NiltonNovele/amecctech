<script setup lang="ts">
// import { motion } from "@motionone/vue";
import { Badge } from "@/components/ui/badge";
import { Button } from "@/components/ui/button";
import { ArrowRight } from "lucide-vue-next";
import { ref } from "vue";

const flipped = ref<number | null>(null);

const benefits = [
  {
    title: "Team Synergy",
    image: "/obama.jpg",
    short: "Work with people who push you forward.",
    detail: "Collaborate with brilliant minds to learn, grow, and bring your best ideas to life.",
  },
  {
    title: "Cool Prizes",
    image: "/obama.jpg",
    short: "Real rewards for real innovation.",
    detail: "Stand a chance to win top-notch tech gear, cash prizes, and career-boosting perks.",
  },
  {
    title: "Tech Exposure",
    image: "/obama.jpg",
    short: "Get noticed by top companies.",
    detail: "AMECCTECH attracts recruiters, tech leaders, and mentors. It’s your spotlight moment.",
  },
];
</script>

<template>
  <section class="container py-20 md:py-32">
    <div class="max-w-screen-xl mx-auto text-center space-y-16 px-4">
      <!-- Badge -->
      <Badge variant="outline" class="text-blue-600 text-sm py-2">
        Why Join the AMECCTECH Hackathon?
      </Badge>

      <!-- Title -->
      <motion.h1
        class="text-4xl md:text-6xl font-bold leading-tight"
        :initial="{ opacity: 0, y: -40 }"
        :animate="{ opacity: 1, y: 0 }"
        transition="{ duration: 0.8, delay: 0.1 }"
      >
        Unleash Your Potential.
        <span
          class="text-transparent bg-gradient-to-r from-blue-500 to-emerald-600 bg-clip-text"
        >
          Build the Future.
        </span>
      </motion.h1>

      <!-- Description -->
      <p class="text-xl text-muted-foreground max-w-3xl mx-auto">
        AMECCTECH isn’t just another hackathon. It’s a launchpad. Here's why you can't miss it:
      </p>

      <!-- Flip Card Grid -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-10 mt-16">
        <div
          v-for="(item, index) in benefits"
          :key="index"
          class="perspective h-[32rem]"
          @click="flipped === index ? flipped = null : flipped = index"
        >
          <div
            class="flip-card w-full h-full transition-transform duration-700 hover:scale-105 hover:shadow-xl"
            :class="{ flipped: flipped === index }"
          >
            <!-- Front Side -->
            <div
              class="flip-card-front p-6 border rounded-xl shadow-md bg-white dark:bg-gray-900 flex flex-col justify-center items-center space-y-6"
            >
              <img
                :src="item.image"
                alt=""
                class="w-48 h-48 object-cover rounded-lg shadow-md"
              />
              <h3 class="text-xl font-bold text-blue-600 text-center">{{ item.title }}</h3>
              <p class="text-base text-muted-foreground text-center">{{ item.short }}</p>
            </div>

            <!-- Back Side -->
            <div
              class="flip-card-back p-8 border rounded-xl shadow-md bg-blue-600 text-white flex flex-col justify-center items-center"
            >
              <h3 class="text-xl font-semibold mb-3 text-center">{{ item.title }}</h3>
              <p class="text-base text-center">{{ item.detail }}</p>
              <span class="text-xs mt-6 opacity-70">(Tap or click again to flip)</span>
            </div>
          </div>
        </div>
      </div>

      <!-- CTA -->
      <div class="mt-24 flex justify-center">
        <Button
          as-child
          class="px-6 py-3 text-lg font-bold group/arrow bg-blue-600 hover:bg-blue-700 transform transition duration-300 ease-in-out hover:scale-105"
        >
          <a href="/register" class="flex items-center">
            Register Now
            <ArrowRight
              class="size-5 ml-2 group-hover/arrow:translate-x-2 group-hover/arrow:opacity-100 opacity-75 transition-all duration-300 ease-in-out"
            />
          </a>
        </Button>
      </div>
    </div>
  </section>
</template>


<style scoped>
.perspective {
  perspective: 1000px;
}

.flip-card {
  transform-style: preserve-3d;
  position: relative;
  width: 100%;
  height: 100%;
}

.flip-card-front,
.flip-card-back {
  backface-visibility: hidden;
  position: absolute;
  width: 100%;
  height: 100%;
  border-radius: 0.75rem;
  overflow: hidden;
}

.flip-card-front {
  z-index: 2;
  transform: rotateY(0deg);
}

.flip-card-back {
  transform: rotateY(180deg);
}

.flipped {
  transform: rotateY(180deg);
}
</style>
