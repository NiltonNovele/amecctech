<script lang="ts" setup>
import { ref, computed } from "vue";
import { useColorMode } from "@vueuse/core";

const mode = useColorMode(); 
const currentMode = computed(() => mode.value); 

import {
  NavigationMenu,
  NavigationMenuContent,
  NavigationMenuItem,
  NavigationMenuLink,
  NavigationMenuList,
  NavigationMenuTrigger,
} from "@/components/ui/navigation-menu";
import {
  Sheet,
  SheetContent,
  SheetFooter,
  SheetHeader,
  SheetTitle,
  SheetTrigger,
} from "@/components/ui/sheet";

import { Button } from "@/components/ui/button";
import { Separator } from "@/components/ui/separator";

import { Menu } from "lucide-vue-next";
import GithubIcon from "@/icons/LinkedInIcon.vue";
import ToggleTheme from "./ToggleTheme.vue";

interface RouteProps {
  href: string;
  label: string;
}

interface FeatureProps {
  title: string;
  description: string;
}

const routeList: RouteProps[] = [
  { href: "#depoimentos", label: "Mentors & Judges" },
  { href: "#equipa", label: "Equipa" },
  { href: "#contacto", label: "Contacto" },
  { href: "/tncs.pdf", label: "Docs" },
];

const featureList: FeatureProps[] = [
  {
    title: "What",
    description:
      "A 48-hour hackathon hosted by TechSolutions and AMECC to promote inovation 2ojvnb43or",
  },
  {
    title: "When & Where",
    description:
      "30th and 31st of August, in CAPE TOWN",
  },
  {
    title: "Details",
    description:
      "The doors for participantes close on the 4/39/9221. Make sure that you and your team have registred.",
  },
  {
    title: "Help",
    description:
      "Any concern, please do not hesitate to reach out to us, or use our built-in chatbot",
  },
];

const isOpen = ref<boolean>(false);
</script>

<template>
  <header
    :class="{
      'shadow-light': currentMode === 'light',
      'shadow-dark': currentMode === 'dark',
      'w-[90%] md:w-[70%] lg:w-[75%] lg:max-w-screen-xl top-5 mx-auto sticky border z-40 rounded-2xl flex justify-between items-center p-2 bg-card shadow-md': true,
    }"
  >
    <!-- Desktop Logo & Name -->
    <a href="/" class="font-bold text-lg flex items-center space-x-2">
      <img src="/logo.jpg" alt="SyncTechX Logo" class="h-9 w-auto" />
      <span>AMECCTECH</span>
    </a>

    <!-- Mobile -->
    <div class="flex items-center lg:hidden">
      <Sheet v-model:open="isOpen">
        <SheetTrigger as-child>
          <Menu @click="isOpen = true" class="cursor-pointer" />
        </SheetTrigger>

        <SheetContent
          side="left"
          class="flex flex-col justify-between rounded-tr-2xl rounded-br-2xl bg-card"
        >
          <div>
            <SheetHeader class="mb-4 ml-4">
              <SheetTitle class="flex items-center space-x-2">
                <a href="/" class="flex items-center space-x-2">
                  <img
                    src="/logo.jpg"
                    alt="AMECCTECH Logo"
                    class="h-9 w-auto"
                  />
                  <span>AMECCTECH</span>
                </a>
              </SheetTitle>
            </SheetHeader>

            <div class="flex flex-col gap-2">
              <Button
                v-for="{ href, label } in routeList"
                :key="label"
                as-child
                variant="ghost"
                class="justify-start text-base"
              >
                <a @click="isOpen = false" :href="href">
                  {{ label }}
                </a>
              </Button>
            </div>
          </div>

          <SheetFooter class="flex-col sm:flex-col justify-start items-start space-y-2 px-4">
            <Separator />
            <ToggleTheme />
            <!-- Enter Button Mobile -->
            <Button
              as-child
              variant="outline"
              class="w-full mt-2"
              @click="isOpen = false"
            >
              <a href="/login">Entrar</a>
            </Button>
          </SheetFooter>
        </SheetContent>
      </Sheet>
    </div>

    <!-- Desktop Navigation -->
    <NavigationMenu class="hidden lg:block">
      <NavigationMenuList>
        <NavigationMenuItem>
          <NavigationMenuTrigger class="bg-card text-base">
            Event
          </NavigationMenuTrigger>
          <NavigationMenuContent>
            <div class="grid w-[600px] grid-cols-2 gap-5 p-4">
              <img
                src="/logo.jpg"
                alt="AMECCTECH"
                class="h-full w-full rounded-md object-cover"
              />
              <ul class="flex flex-col gap-2">
                <li
                  v-for="{ title, description } in featureList"
                  :key="title"
                  class="rounded-md p-3 text-sm hover:bg-muted"
                >
                  <p class="mb-1 font-semibold leading-none text-foreground">
                    {{ title }}
                  </p>
                  <p class="line-clamp-2 text-muted-foreground">
                    {{ description }}
                  </p>
                </li>
              </ul>
            </div>
          </NavigationMenuContent>
        </NavigationMenuItem>

        <NavigationMenuItem>
          <NavigationMenuLink asChild>
            <div class="flex">
              <Button
                v-for="{ href, label } in routeList"
                :key="label"
                as-child
                variant="ghost"
                class="justify-start text-base"
              >
                <a :href="href">
                  {{ label }}
                </a>
              </Button>
            </div>
          </NavigationMenuLink>
        </NavigationMenuItem>
      </NavigationMenuList>
    </NavigationMenu>

    <!-- Desktop Toggle, Social & Enter -->
    <div class="hidden lg:flex items-center space-x-2">
      <ToggleTheme />

      <Button as-child size="sm" variant="ghost" aria-label="LinkedIn">
        <a
          href="https://www.linkedin.com/company/synctechx/"
          target="_blank"
          aria-label="LinkedIn"
        >
          <GithubIcon class="size-5" />
        </a>
      </Button>

      <!-- Enter Button Desktop -->
      <Button as-child size="sm" variant="outline" class="ml-2">
        <a href="/login">Entrar</a>
      </Button>
    </div>
  </header>
</template>

<style scoped>
.shadow-light {
  box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.085);
}

.shadow-dark {
  box-shadow: inset 0 0 5px rgba(255, 255, 255, 0.141);
}
</style>
