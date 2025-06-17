<script setup lang="ts">
import { useColorMode } from "@vueuse/core";
const mode = useColorMode();

import { Badge } from "@/components/ui/badge";
import { Button } from "@/components/ui/button";
import { ArrowRight } from "lucide-vue-next";

// Helper function to split text into span elements for animation
const bounceText = (text: string) => {
  return text.split("").map((char, index) => ({
    char,
    delay: index * 0.1,
  }));
};

const hackathonText = bounceText("AMECCTECH Hackathon");
</script>

<template>
  <section class="container">
    <div class="grid place-items-center lg:max-w-screen-xl gap-8 mx-auto py-20 md:py-32">
      <div class="text-center space-y-8">
        <Badge variant="outline" class="text-sm py-2 text-blue-600">
          <span class="mr-2 text-blue-600">
            <Badge>New</Badge>
          </span>
          <span>Join us at the AMECCTECH Hackathon in Cape Town!</span>
        </Badge>

        <div class="max-w-screen-md mx-auto text-center text-5xl md:text-6xl font-bold leading-tight">
          <h1>
            Empower Your Skills at
            <span
              aria-label="AMECCTECH Hackathon"
              role="text"
              class="text-transparent bg-gradient-to-r from-blue-500 to-emerald-600 bg-clip-text inline-block ml-2"
            >
                <span
              class="text-transparent bg-gradient-to-r from-blue-500 to-emerald-600 bg-clip-text"
              >AMECCTECH Hackathon
            </span>
            </span>
          </h1>
        </div>

        <p class="max-w-screen-sm mx-auto text-xl text-muted-foreground">
          Organized by AMECC and Techsolutions, AMECCTECH is a 48-hour hackathon
          bringing together the brightest minds in Cape Town to innovate and
          create impactful digital solutions.
        </p>

        <div class="space-y-4 md:space-y-0 md:space-x-4 flex flex-col md:flex-row items-center justify-center">
          <Button
            as-child
            class="w-5/6 md:w-1/4 font-bold group/arrow bg-blue-600 hover:bg-blue-700 transform transition duration-300 ease-in-out hover:scale-105 hover:glow"
          >
            <a
              href="https://youtube.com"
              target="_blank"
              rel="noopener noreferrer"
              class="flex items-center"
            >
              Get Started
              <ArrowRight
                class="size-5 ml-2 group-hover/arrow:translate-x-2 group-hover/arrow:opacity-100 opacity-75 transition-all duration-300 ease-in-out"
              />
            </a>
          </Button>

          <Button
            as-child
            variant="secondary"
            class="w-5/6 md:w-1/4 font-bold"
          >
            <a href="https://www.linkedin.com/company/amecc/" target="_blank"
              >View Instagram</a
            >
          </Button>
        </div>
      </div>

      <div class="relative group mt-14">
        <!-- gradient shadow -->
        <div
          class="absolute -top-6 right-12 w-[90%] h-12 lg:h-[80%] bg-blue-600/50 blur-3xl rounded-full img-shadow-animation"
        ></div>

        <img
          class="w-full md:w-[1200px] mx-auto rounded-lg relative leading-none flex items-center border border-t-2 border-t-blue-400/30 img-border-animation"
          :src="mode == 'light' ? '/image.jpg' : '/cpt.jpg'"
          alt="AMECCTECH hackathon dashboard"
          style="max-height: 450px; object-fit: contain;"
        />

        <!-- gradient overlay on image -->
        <div
          class="absolute bottom-0 left-0 w-full h-20 md:h-28 bg-gradient-to-b from-background/0 via-background/50 to-background rounded-lg"
        ></div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Existing animations */
.img-shadow-animation {
  animation-name: img-shadow-animation;
  animation-iteration-count: infinite;
  animation-duration: 2s;
  animation-timing-function: linear;
  animation-direction: alternate;
}

.img-border-animation {
  animation-name: img-border-animation;
  animation-iteration-count: infinite;
  animation-duration: 2s;
  animation-timing-function: linear;
  animation-direction: alternate;
}

@keyframes img-shadow-animation {
  from {
    opacity: 0.5;
    transform: translateY(30px);
  }

  to {
    opacity: 1;
    transform: translateY(0px);
  }
}
@keyframes img-border-animation {
  from {
    border-top-color: rgba(34, 197, 94, 0.1); /* green-500/10 */
  }

  to {
    border-top-color: rgba(34, 197, 94, 0.6); /* green-500/60 */
  }
}

/* New bounce up animation for each letter */
@keyframes bounce-up {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-15%);
  }
}

.animate-bounce-up {
  animation-name: bounce-up;
  animation-duration: 1.2s;
  animation-timing-function: ease-in-out;
  animation-iteration-count: infinite;
  display: inline-block;
}

/* Glowing pulse for the button */
@keyframes glow-pulse {
  0%, 100% {
    box-shadow: 0 0 8px rgba(59, 130, 246, 0.6);
  }
  50% {
    box-shadow: 0 0 20px rgba(59, 130, 246, 1);
  }
}

.hover\:glow:hover {
  animation: glow-pulse 2s infinite;
}
</style>
