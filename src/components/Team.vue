<script setup lang="ts">
import {
  Card,
  CardContent,
  CardHeader,
  CardTitle,
  CardFooter,
} from "@/components/ui/card";

import LinkedInIcon from "@/icons/LinkedInIcon.vue";
import GithubIcon from "@/icons/GithubIcon.vue";
import XIcon from "@/icons/XIcon.vue";

interface TeamProps {
  imageUrl: string;
  firstName: string;
  lastName: string;
  positions: string[];
  socialNetworks: SocialNetworkProps[];
}

interface SocialNetworkProps {
  name: string;
  url: string;
}

const teamList: TeamProps[] = [
  {
    imageUrl: "/obama.jpg",
    firstName: "Barack",
    lastName: "Obama",
    positions: ["Líder de Tecnologia"],
    socialNetworks: [
      {
        name: "LinkedIn",
        url: "https://www.linkedin.com/in/nilton-novele-82211821b/",
      },
      {
        name: "Github",
        url: "https://github.com/NiltonNovele",
      },
      {
        name: "X",
        url: "https://x.com/nilton_novele",
      },
    ],
  },
  {
    imageUrl: "/obama.jpg",
    firstName: "Barack",
    lastName: "Obama",
    positions: ["Líder de Marketing"],
    socialNetworks: [
      {
        name: "LinkedIn",
        url: "https://www.linkedin.com/in/",
      },
      {
        name: "X",
        url: "https://x.com/Biondashirley05",
      },
    ],
  },
  {
    imageUrl: "/obama.jpg",
    firstName: "Barack",
    lastName: "Obama",
    positions: ["Líder de Operações"],
    socialNetworks: [
      {
        name: "LinkedIn",
        url: "https://www.linkedin.com/in/henzel-tibana-a07068211/",
      },
      // {
      //   name: "Github",
      //   url: "https://github.com/leoMirandaa",
      // },
    ],
  },
  {
    imageUrl: "/obama.jpg",
    firstName: "Barack",
    lastName: "Obama",
    positions: ["Líder de Relações Externas"],
    socialNetworks: [
      {
        name: "LinkedIn",
        url: "https://www.linkedin.com/in/anderson-joão-manjate-75abaa31a/",
      },
    ],
  },
];

const socialIcon = (socialName: string) => {
  switch (socialName) {
    case "LinkedIn":
      return LinkedInIcon;

    case "Github":
      return GithubIcon;

    case "X":
      return XIcon;
  }
};

const mentorsList: TeamProps[] = [
  {
    imageUrl: "/obama.jpg",
    firstName: "Alice",
    lastName: "Mentora",
    positions: ["AI Mentor"],
    socialNetworks: [
      {
        name: "LinkedIn",
        url: "https://linkedin.com/in/alice",
      },
    ],
  },
  {
    imageUrl: "/obama.jpg",
    firstName: "Carlos",
    lastName: "Mentor",
    positions: ["UI/UX Mentor"],
    socialNetworks: [
      {
        name: "Github",
        url: "https://github.com/carlosmentor",
      },
    ],
  },
  // Add more mentors here
];
</script>

<template>
  <section id="team" class="container lg:w-[75%] py-24 sm:py-32">
    <div class="text-center mb-8">
      <h2 class="text-lg text-blue-600 text-center mb-2 tracking-wider">
        Panel of jurors
      </h2>

      <h2 class="text-3xl md:text-4xl text-center font-bold">
        Judges
      </h2>
    </div>

    <div
      class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8"
    >
      <Card
        v-for="{
          imageUrl,
          firstName,
          lastName,
          positions,
          socialNetworks,
        } in teamList"
        :key="imageUrl"
        class="bg-muted/60 dark:bg-card flex flex-col h-full overflow-hidden group/hoverimg"
      >
        <CardHeader class="p-0 gap-0">
          <div class="h-full overflow-hidden">
            <img
              :src="imageUrl"
              alt=""
              class="w-full aspect-square object-cover saturate-0 transition-all duration-200 ease-linear size-full group-hover/hoverimg:saturate-100 group-hover/hoverimg:scale-[1.01]"
            />
          </div>
          <CardTitle class="py-6 pb-4 px-6">
            {{ firstName }}
            <span class="text-blue-600">{{ lastName }}</span>
          </CardTitle>
        </CardHeader>

        <CardContent
          v-for="(position, index) in positions"
          :key="index"
          :class="{
            'pb-0 text-muted-foreground': true,
            'pb-4': index === positions.length - 1,
          }"
        >
          {{ position }}<span v-if="index < positions.length - 1">,</span>
        </CardContent>

        <CardFooter class="space-x-4 mt-auto">
          <a
            v-for="{ name, url } in socialNetworks"
            :key="name"
            :href="url"
            target="_blank"
            class="hover:opacity-80 transition-all"
            :aria-label="`Visite nossa página no ${name}`"
          >
            <component :is="socialIcon(name)" />
          </a>
        </CardFooter>
      </Card>
    </div>


    <div class="mt-24">
  <div class="text-center mb-8">
    <h2 class="text-lg text-emerald-600 text-center mb-2 tracking-wider">
      Support Team
    </h2>
    <h2 class="text-2xl md:text-3xl text-center font-semibold">
      Mentors
    </h2>
  </div>

  <div
    class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6"
  >
    <Card
      v-for="{
        imageUrl,
        firstName,
        lastName,
        positions,
        socialNetworks,
      } in mentorsList"
      :key="imageUrl + firstName"
      class="bg-muted/50 dark:bg-card flex flex-col h-full overflow-hidden group/hoverimg border border-muted rounded-md scale-95"
    >
      <CardHeader class="p-0">
        <div class="h-full overflow-hidden">
          <img
            :src="imageUrl"
            alt=""
            class="w-full aspect-square object-cover saturate-0 transition-all duration-200 ease-linear group-hover/hoverimg:saturate-100 group-hover/hoverimg:scale-[1.01]"
          />
        </div>
        <CardTitle class="py-4 px-4 text-base">
          {{ firstName }}
          <span class="text-emerald-600">{{ lastName }}</span>
        </CardTitle>
      </CardHeader>

      <CardContent
        v-for="(position, index) in positions"
        :key="index"
        :class="{
          'pb-0 text-sm text-muted-foreground px-4': true,
          'pb-3': index === positions.length - 1,
        }"
      >
        {{ position }}<span v-if="index < positions.length - 1">,</span>
      </CardContent>

      <CardFooter class="space-x-4 mt-auto px-4 pb-4">
        <a
          v-for="{ name, url } in socialNetworks"
          :key="name"
          :href="url"
          target="_blank"
          class="hover:opacity-80 transition-all"
          :aria-label="`Visite nossa página no ${name}`"
        >
          <component :is="socialIcon(name)" class="w-4 h-4" />
        </a>
      </CardFooter>
    </Card>
  </div>
</div>
  </section>
</template>
