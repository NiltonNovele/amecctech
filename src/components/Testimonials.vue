<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle, CardDescription } from "@/components/ui/card";

const hackathonInfo = {
  theme: "Empregabilidade",
  mission:
    "A missão do Grupo será de desenvolver uma solução inovadora para um tópico a ser revelado no dia do evento dentro do tema, criando um modelo sustentável e viável que poderá impactar o futuro de muitos jovens.",
  howItWorksTitle: "Como funcionará?",
  howItWorksDescription:
    "O evento terá a duração de 2 dias: o primeiro dia será dedicado à elaboração e desenvolvimento da ideia e do trabalho, e o segundo dia será reservado para a apresentação e defesa do projeto.",
  projectRequirementsTitle: "O documento do projeto do grupo deverá incluir:",
  projectRequirements: [
    "Nome do grupo e dos participantes",
    "Problema identificado",
    "Proposta de solução",
    "Estratégia de marketing",
    "Modelo de negócio",
  ],
  juryTitle: "O Júri",
  juryDescription:
    "O projeto será avaliado por especialistas em Marketing, Tecnologia, Finanças, Políticas Públicas e Empreendedorismo.",
  targetAudienceTitle: "Quem pode participar?",
  targetAudienceDescription:
    "Este hackathon é aberto a todos estudantes, mas com um foco especial nos estudantes Moçambicanos residentes em Portugal. Se queres testar as tuas competências, colaborar com mentes criativas e construir soluções para um futuro melhor, este evento é para ti!",
};
</script>

<template>
  <section id="hackathon-info" class="container py-24 sm:py-32">
    <div class="max-w-6xl mx-auto">
      <!-- Wrapper container for all sections -->
      <div class="space-y-24">
        <!-- Tema & Missão -->
        <section class="text-center max-w-4xl mx-auto">
          <h2 class="text-lg text-blue-600 mb-2 tracking-widest font-semibold uppercase">
            Tema & Missão
          </h2>
          <h1 class="text-4xl md:text-5xl font-extrabold mb-6">
            {{ hackathonInfo.theme }}
          </h1>
          <p class="text-lg text-gray-700 dark:text-gray-300 max-w-3xl mx-auto leading-relaxed">
            {{ hackathonInfo.mission }}
          </p>
        </section>

        <!-- How It Works and Image side by side -->
        <section class="lg:flex lg:items-start lg:gap-16">
          <div class="flex-1 space-y-10">
            <Card class="bg-white dark:bg-gray-900 rounded-2xl shadow-lg p-8">
              <CardHeader>
                <CardTitle class="text-2xl font-bold text-blue-800 dark:text-blue-300">
                  {{ hackathonInfo.howItWorksTitle }}
                </CardTitle>
              </CardHeader>
              <CardContent class="text-gray-700 dark:text-gray-300 leading-relaxed text-base">
                {{ hackathonInfo.howItWorksDescription }}
              </CardContent>
            </Card>

            <Card class="bg-white dark:bg-gray-900 rounded-2xl shadow-lg p-8">
              <CardHeader>
                <CardTitle class="text-2xl font-bold text-blue-800 dark:text-blue-300">
                  {{ hackathonInfo.projectRequirementsTitle }}
                </CardTitle>
              </CardHeader>
              <CardContent class="text-gray-700 dark:text-gray-300 leading-relaxed text-base list-inside list-disc">
                <ul>
                  <li v-for="(item, index) in hackathonInfo.projectRequirements" :key="index">
                    {{ item }}
                  </li>
                </ul>
              </CardContent>
            </Card>
          </div>

          <div
            class="mt-12 lg:mt-0 flex-shrink-0 w-full max-w-md mx-auto lg:max-w-lg rounded-3xl overflow-hidden shadow-xl border border-blue-200 dark:border-blue-800"
          >
            <img
              src="/studs.jpg"
              alt="Imagem ilustrativa do Hackathon"
              class="w-full h-auto object-cover"
            />
          </div>
        </section>

        <!-- Jury -->
        <section>
          <Card class="bg-white dark:bg-gray-900 rounded-2xl shadow-lg p-8 max-w-4xl mx-auto">
            <CardHeader>
              <CardTitle class="text-2xl font-bold text-blue-800 dark:text-blue-300">
                {{ hackathonInfo.juryTitle }}
              </CardTitle>
            </CardHeader>
            <CardContent class="text-gray-700 dark:text-gray-300 leading-relaxed text-base">
              {{ hackathonInfo.juryDescription }}
            </CardContent>
          </Card>
        </section>

        <!-- Target Audience -->
        <section>
          <Card class="bg-white dark:bg-gray-900 rounded-2xl shadow-lg p-8 max-w-4xl mx-auto">
            <CardHeader>
              <CardTitle class="text-2xl font-bold text-blue-800 dark:text-blue-300">
                {{ hackathonInfo.targetAudienceTitle }}
              </CardTitle>
            </CardHeader>
            <CardContent class="text-gray-700 dark:text-gray-300 leading-relaxed text-base">
              {{ hackathonInfo.targetAudienceDescription }}
            </CardContent>
          </Card>
        </section>
      </div>
    </div>
  </section>
</template>
