<script setup lang="ts">
import { ref, reactive } from "vue";
import { Button } from "./ui/button";
import { Card, CardHeader, CardContent, CardFooter } from "./ui/card";
import { Label } from "./ui/label";
import { Input } from "./ui/input";
import {
  Select,
  SelectContent,
  SelectGroup,
  SelectItem,
  SelectTrigger,
  SelectValue,
} from "./ui/select";
import { Textarea } from "./ui/textarea";
import { Alert, AlertDescription, AlertTitle } from "@/components/ui/alert";
import { AlertCircle, Building2, Phone, Mail, Clock } from "lucide-vue-next";

const formType = ref<"participant" | "viewer">("participant");

// Participant form state
const contactForm = reactive({
  firstName: "",
  lastName: "",
  email: "",
  phone: "",
  teamName: "",
  teamMembers: "",
  subject: "Desenvolvimento Web",
  message: "",
});

// Viewer form state
const viewerForm = reactive({
  fullName: "",
  email: "",
  ticketDuration: "",
  numberOfPeople: 1,
  paymentMethod: "",
});

const invalidInputForm = ref(false);

const handleSubmit = () => {
  if (formType.value === "participant") {
    const {
      firstName,
      lastName,
      email,
      phone,
      teamName,
      teamMembers,
      subject,
      message,
    } = contactForm;

    const mailToLink = `mailto:nilton.novele@gmail.com?subject=${subject}&body=Olá, sou ${firstName} ${lastName} (${email}, ${phone}).\n\nNome da Equipa: ${teamName}\nMembros: ${teamMembers}\n\n${message}`;
    window.location.href = mailToLink;
  } else {
    const { fullName, email } = viewerForm;
    const mailToLink = `mailto:nilton.novele@gmail.com?subject=Pedido de Bilhete&body=Olá, sou ${fullName} e gostaria de assistir ao evento. Meu e-mail é ${email}.`;
    window.location.href = mailToLink;
  }
};
</script>

<template>
  <section id="contact" class="container py-24 sm:py-32">
    <section class="grid grid-cols-1 md:grid-cols-2 gap-8">
      <!-- Informações de contacto -->
      <div>
        <div class="mb-4">
          <h2 class="text-lg text-blue-500 mb-2 tracking-wider">AMECCTECH 2025</h2>
          <h2 class="text-3xl md:text-4xl font-bold">Join Now</h2>
        </div>
        <p class="mb-8 text-muted-foreground lg:w-5/6">
          Are you ready?
        </p>

        <div class="flex flex-col gap-4">
          <div>
            <div class="flex gap-2 mb-1">
              <Building2 />
              <div class="font-bold">Location</div>
            </div>
            <a
              href="https://www.google.com/maps/place/Cape+Town,+South+Africa"
              target="_blank"
              rel="noopener noreferrer"
              
            >
              📍 Cape Town <span class="text-sm">(clique para ver no mapa)</span>
            </a>

          </div>
          <div>
            <div class="flex gap-2 mb-1">
              <Phone />
              <div class="font-bold">Phone</div>
            </div>
            <div>+27 (12) 345-6789</div>
          </div>
          <div>
            <div class="flex gap-2 mb-1">
              <Mail />
              <div class="font-bold">Email</div>
            </div>
            <div>info@amecctech.com</div>
          </div>
          <div>
            <div class="flex gap-2">
              <Clock />
              <div class="font-bold">Dates</div>
            </div>
            <div>
              <div>30th & 31st August</div>
              <div>08h00 - 16h00</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Formulário -->
      <Card class="bg-muted/60 dark:bg-card">
        <CardHeader>
          <div class="mb-4 text-lg font-semibold">Registration Type</div>
          <div class="flex gap-4">
            <Button
              variant="outline"
              :class="formType === 'participant' ? 'bg-blue-500' : ''"
              @click="formType = 'participant'"
            >
              Participant
            </Button>
            <Button
              variant="outline"
              :class="formType === 'viewer' ? 'bg-blue-500' : ''"
              @click="formType = 'viewer'"
            >
              Viewer
            </Button>
          </div>
        </CardHeader>

        <CardContent>
          <form @submit.prevent="handleSubmit" class="grid gap-4">
            <!-- PARTICIPANT FORM -->
            <template v-if="formType === 'participant'">
              <div class="flex flex-col md:flex-row gap-8">
                <div class="flex flex-col w-full gap-1.5">
                  <Label for="first-name">Name</Label>
                  <Input
                    id="first-name"
                    type="text"
                    placeholder="Nilton"
                    v-model="contactForm.firstName"
                  />
                </div>
                <div class="flex flex-col w-full gap-1.5">
                  <Label for="last-name">Surname</Label>
                  <Input
                    id="last-name"
                    type="text"
                    placeholder="Novele"
                    v-model="contactForm.lastName"
                  />
                </div>
              </div>

              <div class="flex flex-col gap-1.5">
                <Label for="email">Email</Label>
                <Input
                  id="email"
                  type="email"
                  placeholder="nilton@example.com"
                  v-model="contactForm.email"
                />
              </div>

              <div class="flex flex-col gap-1.5">
                <Label for="phone">Phone</Label>
                <Input
                  id="phone"
                  type="text"
                  placeholder="+258 84 123 4567"
                  v-model="contactForm.phone"
                />
              </div>

              <div class="flex flex-col gap-1.5">
                <Label for="team-name">Team Name</Label>
                <Input
                  id="team-name"
                  type="text"
                  placeholder="Os Devzillas"
                  v-model="contactForm.teamName"
                />
              </div>

              <div class="flex flex-col gap-1.5">
                <Label for="team-members" class="flex justify-between items-center">
                  <span>Team Members</span>
                    <a
                      href="/regulamento-de-equipa.pdf"
                      target="_blank"
                      class="text-sm text-blue-600 hover:underline"
                    >
                      Ver regulamento da equipa
                    </a>
                </Label>

                  <Textarea
                    id="team-members"
                    placeholder="Nome dos membros separados por vírgula"
                    v-model="contactForm.teamMembers"
                    />
              </div>


              <div class="flex flex-col gap-1.5">
                <Label for="subject">Specialty (Joint)</Label>
                <Select v-model="contactForm.subject">
                  <SelectTrigger>
                    <SelectValue placeholder="Selecione um assunto" />
                  </SelectTrigger>
                  <SelectContent>
                    <SelectGroup>
                      <SelectItem value="Desenvolvimento Web">Healthcare</SelectItem>
                      <SelectItem value="Desenvolvimento Mobile">Technology</SelectItem>
                      <SelectItem value="Produtos Da SynctechX">Business Management</SelectItem>
                      <SelectItem value="Consultoria Tecnológica">Law & Politics</SelectItem>
                      <SelectItem value="Segurança cibernética e hacking ético">Arts</SelectItem>
                      <SelectItem value="IA e Automação">Science</SelectItem>
                      <SelectItem value="Reclamação / Sugestão">None of the Above</SelectItem>
                    </SelectGroup>
                  </SelectContent>
                </Select>
              </div>

              <div class="flex flex-col gap-1.5">
                <Label for="message">Message</Label>
                <Textarea
                  id="message"
                  placeholder="Anything you would like to let us know..."
                  rows="4"
                  v-model="contactForm.message"
                />
              </div>
            </template>

            <!-- VIEWER FORM -->
            <template v-else>
  <div class="flex flex-col gap-1.5">
    <Label for="viewer-name">Nome completo</Label>
    <Input
      id="viewer-name"
      type="text"
      placeholder="Seu nome"
      v-model="viewerForm.fullName"
    />
  </div>

  <div class="flex flex-col gap-1.5">
    <Label for="viewer-email">Email</Label>
    <Input
      id="viewer-email"
      type="email"
      placeholder="voce@example.com"
      v-model="viewerForm.email"
    />
  </div>

  <div class="flex flex-col gap-1.5">
    <Label for="ticket-days">Duração do bilhete</Label>
    <Select v-model="viewerForm.ticketDuration">
      <SelectTrigger>
        <SelectValue placeholder="Selecione a duração" />
      </SelectTrigger>
      <SelectContent>
        <SelectGroup>
          <SelectItem value="1">1 dia</SelectItem>
          <SelectItem value="2">2 dias</SelectItem>
        </SelectGroup>
      </SelectContent>
    </Select>
  </div>

  <div class="flex flex-col gap-1.5">
    <Label for="num-people">Número de pessoas</Label>
    <Input
      id="num-people"
      type="number"
      placeholder="1"
      v-model="viewerForm.numberOfPeople"
      min="1"
    />
  </div>

  <div class="flex flex-col gap-1.5">
    <Label for="payment-method">Método de pagamento</Label>
    <Select v-model="viewerForm.paymentMethod">
      <SelectTrigger>
        <SelectValue placeholder="Selecione o método" />
      </SelectTrigger>
      <SelectContent>
        <SelectGroup>
          <SelectItem value="door">Pagamento na porta</SelectItem>
          <SelectItem value="online">Online</SelectItem>
          <SelectItem value="eft">Transferência bancária (EFT)</SelectItem>
        </SelectGroup>
      </SelectContent>
    </Select>
  </div>
</template>


            <Alert v-if="invalidInputForm" variant="destructive">
              <AlertCircle class="w-4 h-4" />
              <AlertTitle>Erro</AlertTitle>
              <AlertDescription>
                Há um erro no formulário. Verifique os seus dados.
              </AlertDescription>
            </Alert>

            <Button class="mt-4 bg-blue-600 text-white hover:bg-blue-700">
              {{ formType === "participant" ? "Inscrever equipa" : "Solicitar bilhete" }}
            </Button>
          </form>
        </CardContent>
        <CardFooter />
      </Card>
    </section>
  </section>
</template>
