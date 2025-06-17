<script setup lang="ts">
import { ref } from "vue";

import Navbar from "./components/Navbar.vue";
import Hero from "./components/Hero.vue";
import Benefits from "./components/Benefits.vue";
import Features from "./components/Features.vue";
import Services from "./components/Services.vue";
import HowItWorks from "./components/HowItWorks.vue";
import Sponsors from "./components/Sponsors.vue";
import Testimonials from "./components/Testimonials.vue";
import Team from "./components/Team.vue";
import Pricing from "./components/Pricing.vue";
import Community from "./components/Community.vue";
import Contact from "./components/Contact.vue";
import FAQ from "./components/FAQ.vue";
import Footer from "./components/Footer.vue";
import Blog from "./components/Blog.vue";
import Why from "./components/Why.vue";
import { nextTick } from "vue";

const isChatOpen = ref(false);
const inputMessage = ref("");
const messages = ref<{ from: "user" | "bot"; text: string }[]>([]);

function toggleChat() {
  isChatOpen.value = !isChatOpen.value;
}

function sendMessage() {
  const msg = inputMessage.value.trim();
  if (!msg) return;

  messages.value.push({ from: "user", text: msg });
  inputMessage.value = "";

  // Simulate bot response after a short delay
  setTimeout(() => {
    messages.value.push({
      from: "bot",
      text: `You said: "${msg}". How can I assist you further?`,
    });

    scrollToBottom();
  }, 1000);

  nextTick(() => scrollToBottom());
}

function scrollToBottom() {
  const chatBody = document.getElementById("chat-body");
  if (chatBody) {
    chatBody.scrollTop = chatBody.scrollHeight;
  }
}

function talkToAgent() {
  alert("Connecting to a human agent...");
  // Here you would implement your live agent connection
}
</script>

<template>
  <Navbar />
  <Hero />
  <Sponsors />
  <Benefits />
  <Features />
  <Services />
  <HowItWorks />
  <Testimonials />
  <Team />
  <Community />
  <Pricing />
  <Blog />
  <Contact />
  <Why />
  <FAQ />
  <Footer />

  <!-- Chatbot icon button -->
  <button
    @click="toggleChat"
    aria-label="Toggle Chatbot"
    class="fixed bottom-6 right-6 z-50 flex h-16 w-16 items-center justify-center rounded-full bg-blue-600 text-white shadow-lg hover:bg-blue-700 transition"
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      fill="none"
      stroke="currentColor"
      stroke-width="2"
      stroke-linecap="round"
      stroke-linejoin="round"
      class="h-8 w-8"
      viewBox="0 0 24 24"
    >
      <path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2z" />
    </svg>
  </button>

  <!-- Chatbot window panel -->
  <div
    v-if="isChatOpen"
    class="fixed bottom-20 right-6 z-50 w-96 max-w-full rounded-lg bg-white shadow-xl border border-gray-300 flex flex-col"
  >
    <header
      class="flex justify-between items-center bg-blue-600 text-white px-4 py-3 rounded-t-lg select-none"
    >
      <h2 class="text-lg font-semibold">Chatbot</h2>
      <button
        @click="toggleChat"
        aria-label="Close Chatbot"
        class="text-white hover:text-gray-300 text-2xl font-bold leading-none"
      >
        &times;
      </button>
    </header>

    <main
      id="chat-body"
      class="p-4 flex-1 overflow-y-auto space-y-3 bg-gray-50"
      style="min-height: 320px;"
    >
      <template v-if="messages.length === 0">
        <p class="text-gray-400 italic text-center">
          Say hi! How can I help you today?
        </p>
      </template>

      <div
        v-for="(msg, index) in messages"
        :key="index"
        :class="[
          'max-w-[80%] p-2 rounded-lg',
          msg.from === 'user' ? 'bg-blue-600 text-white self-end' : 'bg-gray-200 text-gray-800 self-start'
        ]"
      >
        {{ msg.text }}
      </div>
    </main>

    <footer class="p-3 border-t border-gray-300 bg-white flex flex-col gap-2 rounded-b-lg">
      <form
        @submit.prevent="sendMessage"
        class="flex gap-2 items-center"
        autocomplete="off"
      >
        <input
          v-model="inputMessage"
          type="text"
          placeholder="Type your message..."
          class="flex-grow rounded border border-gray-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-blue-600"
          autofocus
        />
        <button
          type="submit"
          class="rounded bg-blue-600 px-4 py-2 text-white hover:bg-blue-700 transition"
          aria-label="Send message"
        >
          Send
        </button>
      </form>
      <button
        @click="talkToAgent"
        class="w-full rounded border border-blue-600 text-blue-600 hover:bg-blue-50 transition px-4 py-2 font-semibold"
      >
        Talk to Agent
      </button>
    </footer>
  </div>
</template>

<style scoped>
/* Scrollbar for chat body */
#chat-body::-webkit-scrollbar {
  width: 8px;
}
#chat-body::-webkit-scrollbar-thumb {
  background-color: rgba(0, 0, 0, 0.1);
  border-radius: 4px;
}
#chat-body::-webkit-scrollbar-track {
  background: transparent;
}
</style>