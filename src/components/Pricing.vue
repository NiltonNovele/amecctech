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

import { ref } from "vue";

interface SpeakerProps {
  imageUrl: string;
  firstName: string;
  lastName: string;
  titles: string[];
  socialNetworks: SocialNetworkProps[];
  whoIs: string;
  whyHimHer: string;
  willShare: string;
}

interface SocialNetworkProps {
  name: string;
  url: string;
}

const speakersList: SpeakerProps[] = [
  {
    imageUrl: "/obama.jpg",
    firstName: "Sarah",
    lastName: "Johnson",
    titles: ["AI Researcher", "Keynote Speaker"],
    socialNetworks: [
      { name: "LinkedIn", url: "https://linkedin.com/in/sarahjohnson" },
      { name: "X", url: "https://x.com/sarah_johnson" },
    ],
    whoIs: "Sarah is a leading AI researcher with 10 years experience in machine learning.",
    whyHimHer: "Chosen for her pioneering work in deep learning and ethical AI.",
    willShare: "She will share insights on the future of AI and responsible innovation.",
  },
  {
    imageUrl: "/obama.jpg",
    firstName: "David",
    lastName: "Miller",
    titles: ["Cybersecurity Expert"],
    socialNetworks: [
      { name: "LinkedIn", url: "https://linkedin.com/in/davidmiller" },
      { name: "Github", url: "https://github.com/davidmiller" },
    ],
    whoIs: "David specializes in protecting critical infrastructure from cyber threats.",
    whyHimHer: "Known for his innovative approaches to threat detection.",
    willShare: "David will explain emerging trends in cybersecurity defense.",
  },
  {
    imageUrl: "/obama.jpg",
    firstName: "Aisha",
    lastName: "Khan",
    titles: ["Software Engineer", "Panelist"],
    socialNetworks: [{ name: "LinkedIn", url: "https://linkedin.com/in/aishakhan" }],
    whoIs: "Aisha builds scalable cloud platforms for major tech companies.",
    whyHimHer: "A rising star recognized for her open source contributions.",
    willShare: "She will discuss modern cloud architectures and DevOps.",
  },
  {
    imageUrl: "/obama.jpg",
    firstName: "Tom",
    lastName: "Nguyen",
    titles: ["Product Manager"],
    socialNetworks: [
      { name: "LinkedIn", url: "https://linkedin.com/in/tomnguyen" },
      { name: "X", url: "https://x.com/tom_nguyen" },
    ],
    whoIs: "Tom leads cross-functional teams to deliver impactful products.",
    whyHimHer: "Selected for his expertise in agile development.",
    willShare: "He will share best practices in product strategy and management.",
  },
  {
    imageUrl: "/obama.jpg",
    firstName: "Maria",
    lastName: "Lopez",
    titles: ["Data Scientist"],
    socialNetworks: [
      { name: "LinkedIn", url: "https://linkedin.com/in/marialopez" },
      { name: "Github", url: "https://github.com/marialopez" },
    ],
    whoIs: "Maria analyzes complex datasets to drive business insights.",
    whyHimHer: "Her work has transformed data-driven decision making.",
    willShare: "Maria will explore advanced data analytics techniques.",
  },
  {
    imageUrl: "/obama.jpg",
    firstName: "James",
    lastName: "Smith",
    titles: ["CTO", "Guest Speaker"],
    socialNetworks: [{ name: "LinkedIn", url: "https://linkedin.com/in/jamessmith" }],
    whoIs: "James oversees technology direction at a fast-growing startup.",
    whyHimHer: "Experienced in scaling tech teams and systems.",
    willShare: "He will discuss leadership in tech and innovation.",
  },
  {
    imageUrl: "/obama.jpg",
    firstName: "Olivia",
    lastName: "Brown",
    titles: ["UX Designer"],
    socialNetworks: [
      { name: "LinkedIn", url: "https://linkedin.com/in/oliviabrown" },
      { name: "X", url: "https://x.com/oliviab" },
    ],
    whoIs: "Olivia creates intuitive user experiences with a human-centered approach.",
    whyHimHer: "Renowned for her award-winning designs.",
    willShare: "She will talk about the future of UX design.",
  },
  {
    imageUrl: "/obama.jpg",
    firstName: "Liam",
    lastName: "Wilson",
    titles: ["Entrepreneur"],
    socialNetworks: [{ name: "LinkedIn", url: "https://linkedin.com/in/liamwilson" }],
    whoIs: "Liam founded multiple successful tech startups.",
    whyHimHer: "His visionary leadership has inspired many.",
    willShare: "Liam will share lessons learned in entrepreneurship.",
  },
];

const hoveredIndex = ref<number | null>(null);

const socialIcon = (socialName: string) => {
  switch (socialName) {
    case "LinkedIn":
      return LinkedInIcon;
    case "Github":
      return GithubIcon;
    case "X":
      return XIcon;
    default:
      return null;
  }
};

const toggleDetails = (index: number) => {
  hoveredIndex.value = hoveredIndex.value === index ? null : index;
};
</script>

<template>
  <section id="speakers" class="container lg:w-[75%] py-24 sm:py-32 relative">
    <div class="text-center mb-8">
      <h2 class="text-lg text-blue-600 mb-2 tracking-wider">Speakers</h2>
      <h2 class="text-3xl md:text-4xl font-bold">Meet Our Speakers</h2>
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8 relative">
      <Card
        v-for="(
          {
            imageUrl,
            firstName,
            lastName,
            titles,
            socialNetworks,
            whoIs,
            whyHimHer,
            willShare,
          },
          index
        ) in speakersList"
        :key="imageUrl + index"
        class="bg-muted/60 dark:bg-card flex flex-col h-full overflow-hidden group/hoverimg relative cursor-pointer"
        @click="toggleDetails(index)"
      >
        <CardHeader class="p-0 gap-0">
          <div class="h-full overflow-hidden">
            <img
              :src="imageUrl"
              alt=""
              class="w-full aspect-square object-cover saturate-0 transition-all duration-200 ease-linear group-hover/hoverimg:saturate-100 group-hover/hoverimg:scale-[1.01]"
            />
          </div>
          <CardTitle class="py-6 pb-4 px-6 select-none">
            {{ firstName }} <span class="text-blue-600">{{ lastName }}</span>
          </CardTitle>
        </CardHeader>

        <CardContent
          v-for="(title, indexTitle) in titles"
          :key="indexTitle"
          :class="{
            'pb-0 text-muted-foreground': true,
            'pb-4': indexTitle === titles.length - 1,
          }"
        >
          {{ title }}<span v-if="indexTitle < titles.length - 1">,</span>
        </CardContent>

        <CardFooter class="space-x-4 mt-auto">
          <a
            v-for="{ name, url } in socialNetworks"
            :key="name"
            :href="url"
            target="_blank"
            class="hover:opacity-80 transition-all"
            :aria-label="`Visit ${firstName} on ${name}`"
            @click.stop
          >
            <component :is="socialIcon(name)" />
          </a>
        </CardFooter>

        <!-- Click-to-toggle detail box -->
        <transition name="fade">
          <div
            v-if="hoveredIndex === index"
            class="absolute top-0 left-full ml-4 w-80 bg-white dark:bg-gray-900 shadow-lg rounded-md p-6 text-sm z-50"
            style="min-height: 350px;"
          >
            <h3 class="text-lg font-semibold mb-2">
              {{ firstName }} {{ lastName }}
            </h3>
            <p class="mb-2"><strong>Who is {{ firstName }}?</strong></p>
            <p class="mb-4">{{ whoIs }}</p>

            <p class="mb-2"><strong>Why {{ firstName }}?</strong></p>
            <p class="mb-4">{{ whyHimHer }}</p>

            <p class="mb-2"><strong>What will {{ firstName }} share?</strong></p>
            <p>{{ willShare }}</p>
          </div>
        </transition>
      </Card>
    </div>
  </section>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.25s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
