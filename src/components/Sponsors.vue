<script setup lang="ts">
import { Marquee } from "@selemondev/vue3-marquee";
import "@selemondev/vue3-marquee/dist/style.css";

import {
  Crown,
  Vegan,
  Ghost,
  Puzzle,
  Squirrel,
  Cookie,
  Drama,
} from "lucide-vue-next";

interface sponsorsProps {
  icon: string;
  name: string;
}

// const sponsors: sponsorsProps[] = [
//   {
//     icon: "crown",
//     name: "KinesisMz",
//   },
//   {
//     icon: "vegan",
//     name: "KinesisMz",
//   },
//   {
//     icon: "ghost",
//     name: "KinesisMz",
//   },
//   {
//     icon: "puzzle",
//     name: "KinesisMz",
//   },
//   {
//     icon: "squirrel",
//     name: "KinesisMz",
//   },
//   {
//     icon: "cookie",
//     name: "KinesisMz",
//   },
//   {
//     icon: "drama",
//     name: "KinesisMz",
//   },
// ];
const sponsors: sponsorsProps[] = [
  { icon: "puzzle", name: "StandardBank" },
  { icon: "ghost", name: "NedBank" },
  { icon: "cookie", name: "KPMG" },
  { icon: "crown", name: "MISAU" },
  { icon: "vegan", name: "AMECC" },
  { icon: "squirrel", name: "TechSolutions" },
  { icon: "drama", name: "StefanuttiStocks" },
];

const iconMap: Record<
  string,
  | typeof Crown
  | typeof Vegan
  | typeof Ghost
  | typeof Puzzle
  | typeof Squirrel
  | typeof Cookie
  | typeof Drama
> = {
  crown: Crown,
  vegan: Vegan,
  ghost: Ghost,
  puzzle: Puzzle,
  squirrel: Squirrel,
  cookie: Cookie,
  drama: Drama,
};
</script>

<template>
  <section id="sponsors" class="max-w-[75%] mx-auto pb-24 sm:pb-32">
    <h2 class="text-lg md:text-xl text-center mb-6">Sponsors & Partners</h2>

    <div class="mx-auto">
      <Marquee
        class="gap-[3rem]"
        :pauseOnHover="true"
        :fade="true"
        innerClassName="gap-[3rem]"
      >
        <div v-for="{ icon, name } in sponsors" :key="name">
          <div class="flex items-center text-xl md:text-2xl font-medium">
            <component :is="iconMap[icon]" class="mr-2" stroke-width="3" />
            {{ name }}
          </div>
        </div>
      </Marquee>
    </div>
  </section>
</template>
