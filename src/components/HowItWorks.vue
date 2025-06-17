<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Badge } from "@/components/ui/badge";

interface EventStep {
  badgeTitle: string;
  title: string;
  description: string;
  image?: string;
  icon?: string; // optional icon name if you want to add icons later
}

const eventSteps: EventStep[] = [
  {
    badgeTitle: "Grupos",
    title: "Formação de Equipas",
    description:
      "10 grupos com 3 a 5 participantes, preparados para trabalhar juntos na criação de soluções inovadoras para Moçambique.",
    image: "/groups.png",
  },
  {
    badgeTitle: "Mentores",
    title: "Apoio Especializado",
    description:
      "Cada grupo será acompanhado por mentores experientes que fornecerão orientação técnica e estratégica durante todo o evento.",
    image: "/mentors.png",
  },
  {
    badgeTitle: "Desenvolvimento",
    title: "Criação e Inovação",
    description:
      "Durante o hackathon, os grupos desenvolverão as suas ideias, combinando talento e criatividade para resolver desafios reais.",
    image: "/development.png",
  },
  {
    badgeTitle: "Apresentação",
    title: "Defesa das Soluções",
    description:
      "Cada grupo terá 15 minutos para apresentar e defender a sua solução perante um júri de especialistas.",
    image: "/presentation.png",
  },
  {
    badgeTitle: "Local",
    title: "Evento Presencial",
    description:
      "O local será acessível e confortável, proporcionando o ambiente ideal para colaboração e criatividade.",
    image: "/venue.png",
  },
  {
    badgeTitle: "Limite",
    title: "Vagas Limitadas",
    description:
      "Para garantir qualidade e atenção personalizada, as vagas são limitadas a 50 participantes.",
    image: "/limit.png",
  },
];
</script>

<template>
  <section id="how-event-works" class="container py-24 sm:py-32">
    <div class="text-center mb-12">
      <h2 class="text-lg text-blue-600 mb-2 tracking-widest font-semibold uppercase">
        Como Vai Funcionar
      </h2>
      <h1 class="text-4xl md:text-5xl font-extrabold max-w-3xl mx-auto">
        Passo-a-Passo do Evento Hackathon
      </h1>
    </div>

    <div class="lg:w-[80%] mx-auto relative">
      <div
        v-for="(step, index) in eventSteps"
        :key="step.title"
        :class="[
          'flex items-center mb-12 gap-8',
          index % 2 !== 0 ? 'flex-row-reverse' : 'flex-row',
          'sm:gap-16',
        ]"
      >
        <Card class="flex-1 bg-white dark:bg-gray-900 rounded-2xl shadow-lg p-8">
          <CardHeader>
            <Badge class="bg-blue-600 text-white mb-4 inline-block px-4 py-1 rounded-full text-sm font-semibold tracking-wide">
              {{ step.badgeTitle }}
            </Badge>
            <CardTitle class="text-2xl font-bold text-blue-800 dark:text-blue-300 mb-3">
              {{ step.title }}
            </CardTitle>
          </CardHeader>
          <CardContent class="text-gray-700 dark:text-gray-300 text-base leading-relaxed">
            {{ step.description }}
          </CardContent>
        </Card>

        <div class="flex-shrink-0 w-[160px] sm:w-[240px] lg:w-[280px]">
          <img
            :src="step.image"
            :alt="`Imagem sobre ${step.title}`"
            class="rounded-xl shadow-md object-cover w-full h-auto"
          />
        </div>
      </div>
    </div>

    <!-- Optional: A clear summary card or callout -->
    <div class="max-w-3xl mx-auto mt-20 p-8 bg-blue-50 dark:bg-blue-900 rounded-xl text-center shadow-lg">
      <h3 class="text-3xl font-bold mb-4 text-blue-700 dark:text-blue-300">
        Pronto para participar?
      </h3>
      <p class="text-lg text-blue-800 dark:text-blue-200 max-w-xl mx-auto mb-6">
        Junte-se a nós e faça parte da transformação, criando soluções reais para os desafios de Moçambique.
      </p>
      <button
        type="button"
        class="px-10 py-4 bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 active:scale-95 text-white font-bold rounded-full shadow-lg transition-transform duration-150"
      >
        Inscreva-se Agora
      </button>
    </div>
  </section>
</template>

<style scoped>
/* Smooth hover for cards */
.card:hover {
  transform: translateY(-6px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
</style>
