<script setup lang="ts">
import { ref } from "vue";
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { ChevronDown, ChevronUp } from "lucide-vue-next";

interface ScheduleItem {
  time: string;
  title: string;
  description: string;
}

const day1Schedule: ScheduleItem[] = [
  { time: "08:15 - 09:00", title: "Chegada dos Participantes", description: "Receção e registo dos participantes." },
  { time: "09:00 - 10:00", title: "Discurso de Abertura", description: "Boas-vindas e introdução ao evento." },
  { time: "10:00 - 10:30", title: "Apresentação do Desafio", description: "Divulgação do tema e objetivos do hackathon." },
  { time: "10:30 - 11:00", title: "Coffee Break", description: "Intervalo para café e networking informal." },
  { time: "11:00 - 11:45", title: "Palestra de Sustentabilidade", description: "Discussão sobre práticas sustentáveis em tecnologia." },
  { time: "11:45 - 12:15", title: "Palestra de Marketing", description: "Dicas sobre como apresentar e vender ideias." },
  { time: "12:15 - 14:00", title: "Brainstorming e Planeamento", description: "Desenvolvimento inicial das ideias em equipa." },
  { time: "13:00 - 14:00", title: "Validação da Ideia", description: "Testes preliminares e refinamento das propostas." },
  { time: "14:00 - 15:00", title: "Almoço", description: "Pausa para refeição." },
  { time: "15:00 - 18:30", title: "Desenvolvimento do Projeto", description: "Construção dos protótipos pelos participantes." },
  { time: "18:20 - 18:30", title: "Submissão dos Rascunhos", description: "Envio inicial dos projetos." },
  { time: "18:30 - 18:45", title: "Coffee Break", description: "Pausa rápida com bebidas e snacks." },
  { time: "18:45 - 19:00", title: "Considerações Finais", description: "Fecho do primeiro dia e orientações para o dia seguinte." },
  { time: "19:00 - 20:00", title: "Networking", description: "Interação informal entre participantes e mentores." },
];

const day2Schedule: ScheduleItem[] = [
  { time: "08:30 - 09:00", title: "Chegada dos Participantes", description: "Receção para o segundo dia." },
  { time: "09:00 - 09:15", title: "Recapitulação do Dia Anterior", description: "Resumo e pontos principais do primeiro dia." },
  { time: "09:15 - 10:00", title: "Workshop: Como Fazer um Pitch que Convence", description: "Com Arafat Cossa." },
  { time: "10:00 - 11:30", title: "Refinamento do Protótipo e Submissão", description: "Ajustes finais e entrega dos projetos." },
  { time: "11:30 - 11:45", title: "Coffee Break", description: "Intervalo para café." },
  { time: "11:45 - 13:30", title: "Apresentações (1ª Parte)", description: "Apresentação dos primeiros projetos." },
  { time: "13:30 - 14:30", title: "Almoço", description: "Pausa para refeição." },
  { time: "14:30 - 16:00", title: "Apresentações (2ª Parte)", description: "Continuação das apresentações." },
  { time: "16:00 - 16:30", title: "Deliberação dos Jurados | Coffee Break", description: "Tempo para os jurados decidirem os vencedores." },
  { time: "16:30 - 16:45", title: "Premiação", description: "Entrega de prémios aos melhores projetos." },
  {
    time: "16:45 - 17:00",
    title: "Encerramento Oficial",
    description: "Participação de Pedro Alucuamala (Cônsul Geral), Presidente da AEMOPorto e CEO da Techsolutions.",
  },
  { time: "17:00 - 18:00", title: "Networking", description: "Encerramento com socialização e troca de contactos." },
];

const currentDay = ref<1 | 2>(1);
const expandedIndex = ref<number | null>(null);

const toggleDay = (day: 1 | 2) => {
  currentDay.value = day;
  expandedIndex.value = null;
};

const toggleDescription = (index: number) => {
  expandedIndex.value = expandedIndex.value === index ? null : index;
};
</script>

<template>
  <section id="schedule" class="container py-24 sm:py-32">
    <h2 class="text-lg text-blue-600 text-center mb-2 tracking-wider">
      Cronograma
    </h2>
    <h2 class="text-3xl md:text-4xl text-center font-bold mb-10">
      Agenda do Evento
    </h2>

    <div class="flex flex-col md:flex-row md:items-start gap-6">
      <!-- Toggle Buttons Left -->
      <div class="flex md:flex-col justify-center md:justify-start gap-4">
        <button
          @click="toggleDay(1)"
          :class="[
            'py-2 px-4 rounded font-semibold transition w-full text-center',
            currentDay === 1 ? 'bg-blue-600 text-white' : 'bg-gray-200 dark:bg-gray-700'
          ]"
        >
          Dia 1<br /><span class="text-sm font-normal">Sábado, 05 de Abril</span>
        </button>
        <button
          @click="toggleDay(2)"
          :class="[
            'py-2 px-4 rounded font-semibold transition w-full text-center',
            currentDay === 2 ? 'bg-blue-600 text-white' : 'bg-gray-200 dark:bg-gray-700'
          ]"
        >
          Dia 2<br /><span class="text-sm font-normal">Domingo, 06 de Abril</span>
        </button>
      </div>

      <!-- Schedule Cards Right -->
      <div class="grid gap-4 flex-1 max-w-xl"> 
          <Card
          v-for="(item, index) in (currentDay === 1 ? day1Schedule : day2Schedule)"
          :key="index"
          class="bg-muted/60 dark:bg-card relative p-3" 
          >
          <CardHeader @click="toggleDescription(index)" class="cursor-pointer flex justify-between items-center p-0"> 
            <div>
              <p class="text-blue-600 text-sm font-medium">{{ item.time }}</p> 
              <CardTitle class="text-base">{{ item.title }}</CardTitle> 
            </div>
            <component :is="expandedIndex === index ? ChevronUp : ChevronDown" class="text-blue-600 size-4" />
          </CardHeader>
        <CardContent v-if="expandedIndex === index" class="text-muted-foreground text-sm p-0 pt-2">
          {{ item.description }}
        </CardContent>
        </Card>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Optional: add smoother animations */
</style>
