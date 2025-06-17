<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";

import {
  Users2,
  UserCheck,
  Clock,
  MapPin,
  Users,
  Award,
} from "lucide-vue-next";

const iconMap: Record<string, any> = {
  users2: Users2,
  userCheck: UserCheck,
  clock: Clock,
  mapPin: MapPin,
  users: Users,
  award: Award,
};

const hackathonInfo = {
  title: "Hackathon AMECCTECH",
  subtitle: "Inovação para a Empregabilidade",
  description:
    "Estás pronto para transformar desafios em oportunidades? Junta-te ao Hackathon AEMOPorto x TechSolutions, um evento inovador aberto a todos estudantes, com um foco especial nos estudantes Moçambicanos residentes em Portugal. O objetivo é desafiar-te a criar soluções concretas para uma das temáticas mais desafiadoras da atualidade em Moçambique: A Empregabilidade.",
  details: [
    {
      icon: "users2",
      title: "Grupos",
      description: "10 grupos de 3 a 5 participantes a trabalhar numa solução inovadora.",
    },
    {
      icon: "userCheck",
      title: "Mentoria",
      description: "Mentoria especializada com profissionais presentes no evento.",
    },
    {
      icon: "clock",
      title: "Apresentação",
      description: "15 minutos para defesa da ideia perante um júri de especialistas.",
    },
    {
      icon: "mapPin",
      title: "Local do Evento",
      description: "A ser confirmado - em local acessível e confortável.",
    },
    {
      icon: "userCheck",
      title: "Vagas Limitadas",
      description: "Máximo 50 participantes.",
    },
    {
      icon: "users",
      title: "Participantes por Grupo",
      description: "3 a 5 participantes válidos para cada grupo.",
    },
    {
      icon: "award",
      title: "Mentores",
      description: "10 mentores para acompanhamento dedicado de cada grupo.",
    },
  ],
};
</script>

<template>
  <section
    id="hackathon"
    class="min-h-screen bg-gradient-to-b from-blue-50 to-white dark:from-gray-900 dark:to-gray-800 py-24 px-6 sm:px-12 md:px-20"
  >
    <!-- Header -->
    <div class="max-w-4xl mx-auto text-center mb-20">
      <h1
        class="text-5xl sm:text-6xl font-extrabold text-blue-700 dark:text-blue-400 mb-4 leading-tight drop-shadow-sm"
      >
        {{ hackathonInfo.title }}
      </h1>
      <h2
        class="text-2xl sm:text-3xl font-semibold text-blue-600 dark:text-blue-300 mb-8 tracking-wide"
      >
        {{ hackathonInfo.subtitle }}
      </h2>
      <p
        class="text-lg sm:text-xl text-gray-700 dark:text-gray-300 max-w-3xl mx-auto leading-relaxed"
      >
        {{ hackathonInfo.description }}
      </p>
    </div>

    <!-- Details grid -->
    <div
      class="grid gap-10 sm:grid-cols-2 lg:grid-cols-3 max-w-6xl mx-auto mb-20"
    >
      <Card
        v-for="(detail, idx) in hackathonInfo.details"
        :key="idx"
        class="flex flex-col items-center text-center p-10 bg-white dark:bg-gray-900 rounded-2xl shadow-md hover:shadow-2xl transition-shadow transform hover:-translate-y-1 duration-300 cursor-pointer"
      >
        <component
          :is="iconMap[detail.icon]"
          class="text-blue-600 dark:text-blue-400 w-16 h-16 mb-5 drop-shadow"
        />
        <h3 class="text-2xl font-semibold mb-3 text-blue-800 dark:text-blue-300">
          {{ detail.title }}
        </h3>
        <p class="text-gray-600 dark:text-gray-400 text-base leading-relaxed">
          {{ detail.description }}
        </p>
      </Card>
    </div>

    <!-- Call to action -->
    <div class="max-w-3xl mx-auto text-center border-t border-blue-300 dark:border-blue-700 pt-16">
      <p
        class="text-gray-700 dark:text-gray-300 text-lg sm:text-xl leading-relaxed max-w-xl mx-auto"
      >
        As vagas são limitadas para garantir qualidade e atenção personalizada a cada grupo.
        Não percas a oportunidade de fazer parte de uma experiência que pode transformar o teu futuro.
      </p>
      <button
        type="button"
        class="mt-12 px-10 py-4 bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 active:scale-95 active:shadow-lg text-white font-bold rounded-full shadow-lg transition-transform duration-150 focus:outline-none focus:ring-4 focus:ring-blue-400 focus:ring-opacity-50"
      >
        Inscreve-te Agora
      </button>
    </div>
  </section>
</template>

<style scoped>
/* Smooth card hover scaling */
.card-hover-scale:hover {
  transform: scale(1.05);
  transition: transform 0.25s ease;
}
</style>
