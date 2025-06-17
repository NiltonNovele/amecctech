<script setup lang="ts">
import {
  Card,
  CardHeader,
  CardTitle,
  CardFooter,
  CardContent,
} from "@/components/ui/card";

import { Button } from "@/components/ui/button";
import { Mail } from "lucide-vue-next";
import { ref } from "vue";

const email = ref("");
const subscribe = () => {
  if (!email.value) {
    alert("Por favor, insira um email válido.");
    return;
  }

  // Aqui você pode fazer uma chamada para backend ou API
  alert(`Subscrito com sucesso: ${email.value}`);
  email.value = "";
};
</script>

<template>
  <section id="newsletter" class="py-12">
    <hr />
    <div class="container py-20 sm:py-20">
      <div class="lg:w-[60%] mx-auto">
        <Card
          class="bg-background shadow-none text-center flex flex-col items-center justify-center border-0"
        >
          <CardHeader>
            <CardTitle class="text-4xl md:text-5xl font-bold">
              <Mail class="w-16 h-16 m-auto mb-4 text-blue-600" />
              Subscreva-se à nossa
              <span
                class="text-transparent bg-gradient-to-r from-blue-600 to-blue-400 bg-clip-text"
              >
                Newsletter
              </span>
            </CardTitle>
          </CardHeader>

          <CardContent class="lg:w-[80%] text-xl text-muted-foreground">
            Fique atualizado com as nossas últimas novidades e dicas
            exclusivas. Subscreva agora e não perca nada! 📩
          </CardContent>

          <CardFooter
            class="w-full flex flex-col sm:flex-row gap-4 justify-center px-6 mt-4"
          >
            <input
              v-model="email"
              type="email"
              placeholder="Seu email"
              class="text-black w-full sm:w-2/3 px-4 py-3 rounded-xl border border-blue-300 focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
            <Button
              class="bg-blue-600 hover:bg-blue-700 text-white px-6 py-3 rounded-xl"
              @click="subscribe"
            >
              Subscrever
            </Button>
          </CardFooter>
        </Card>
      </div>
    </div>
    <hr />
  </section>
</template>
