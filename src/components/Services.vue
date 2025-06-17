<script setup lang="ts">
import {
  Card,
  CardDescription,
  CardHeader,
  CardTitle,
} from "@/components/ui/card";

import { Badge } from "@/components/ui/badge";

enum ProService {
  YES = 1,
  NO = 0,
}

interface ServiceProps {
  title: string;
  pro: ProService;
  description: string;
}

// Tech Solutions services
const techServices: ServiceProps[] = [
  {
    title: "Custom Software Development",
    description:
      "We create tailored software solutions to meet your business’s unique needs.",
    pro: ProService.NO,
  },
  {
    title: "Website Development & Maintenance",
    description:
      "We design modern, responsive, and optimized websites with ongoing support to ensure top performance.",
    pro: ProService.NO,
  },
];

// AMECC specific services or programs
const ameccServices: ServiceProps[] = [
  {
    title: "Student Mentorship Programs",
    description:
      "Guidance and support to Mozambican students to excel academically and socially abroad.",
    pro: ProService.YES,
  },
  {
    title: "Cultural Integration Activities",
    description:
      "Organized events and initiatives to foster cultural exchange and community building.",
    pro: ProService.NO,
  },
];

const techShortDesc =
  "Innovative technology services designed to boost your business efficiency and growth.";

const ameccShortDesc =
  "Connecting and supporting Mozambican students abroad to thrive academically and socially.";

const ameccDescription =
  "AMECC is a dedicated institution focused on empowering the Mozambican student community abroad, fostering cultural integration, academic excellence, and social support through various programs and initiatives.";

const techDescription ="Tech Solutions is a dynamic service provider committed to empowering businesses through tailored digital innovations, fostering operational efficiency, scalable growth, and seamless integration with modern technology platforms.";

const viewMoreTech = () => {
  window.location.href = "https://techsolutions.co.mz"; // replace with your real Tech Solutions URL
};

const viewMoreAmecc = () => {
  window.location.href = "https://amecc.vercel.app"; // replace with your real AMECC URL
};

</script>

<template>
  <section id="services" class="container py-24 sm:py-32">
    <h2 class="text-lg text-blue-600 text-center mb-2 tracking-wider">
      Organization
    </h2>

    <h2 class="text-3xl md:text-4xl text-center font-bold mb-12">
      Who we are
    </h2>

    <div
      class="flex flex-col lg:flex-row gap-12 lg:gap-16 max-w-7xl mx-auto"
    >
      <!-- Tech Solutions -->
      <div class="flex-1 flex flex-col">
        <h3 class="text-2xl font-semibold mb-6">Tech Solutions</h3>

        <!-- Image + short description -->
        <img
          src="/tech.jpg"
          alt="Tech Solutions"
          class="w-full max-w-md mx-auto rounded-lg mb-4 object-cover aspect-[16/9]"
        />
        <p class="text-muted-foreground mb-8 text-center max-w-md mx-auto">
          {{ techShortDesc }}
        </p>

        <p class="text-muted-foreground mb-8 leading-relaxed max-w-md mx-auto">
          {{ techDescription }}
        </p>

        <div class="grid gap-6">
          <Card
            v-for="({ title, description, pro }) in techServices"
            :key="title"
            class="bg-muted/60 dark:bg-card h-full relative"
          >
            <CardHeader>
              <CardTitle>{{ title }}</CardTitle>
              <CardDescription>{{ description }}</CardDescription>
            </CardHeader>
            <Badge
              v-if="pro === ProService.YES"
              variant="secondary"
              class="absolute -top-2 -right-3"
              >PRO</Badge
            >
          </Card>
        </div>

        <button
          @click="viewMoreTech"
          class="mt-8 self-center bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-6 rounded transition"
        >
          View More
        </button>
      </div>

      <!-- Vertical separator -->
      <div
        class="hidden lg:block border-l border-gray-300 dark:border-gray-700 mx-8"
        aria-hidden="true"
      ></div>

      <!-- AMECC Description -->
      <div class="flex-1 flex flex-col justify-between">
        <h3 class="text-2xl font-semibold mb-6">AMECC</h3>

        <!-- Image + short description -->
        <img
          src="/studs.jpg"
          alt="AMECC Community"
          class="w-full max-w-md mx-auto rounded-lg mb-4 object-cover aspect-[16/9]"
        />
        <p class="text-muted-foreground mb-8 text-center max-w-md mx-auto leading-relaxed">
          {{ ameccShortDesc }}
        </p>

        <p class="text-muted-foreground mb-8 leading-relaxed max-w-md mx-auto">
          {{ ameccDescription }}
        </p>

        <div class="grid gap-6">
          <Card
            v-for="({ title, description, pro }) in ameccServices"
            :key="title"
            class="bg-muted/60 dark:bg-card h-full relative"
          >
            <CardHeader>
              <CardTitle>{{ title }}</CardTitle>
              <CardDescription>{{ description }}</CardDescription>
            </CardHeader>
            <Badge
              v-if="pro === ProService.YES"
              variant="secondary"
              class="absolute -top-2 -right-3"
              >PRO</Badge
            >
          </Card>
        </div>

        <button
          @click="viewMoreAmecc"
          class="self-start bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-6 rounded transition"
        >
          View More
        </button>
      </div>
    </div>
  </section>
</template>
