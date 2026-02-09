<script setup lang="ts">
import { ref } from 'vue'
import { Zap, Sun, Cog } from 'lucide-vue-next'

const services = ref([
  {
    icon: Zap,
    title: 'Instalaciones Eléctricas',
    description: 'Sistemas industriales, comerciales, residenciales y plantas de tratamiento',
    items: [
      'Sistemas industriales',
      'Edificios comerciales',
      'Viviendas residenciales',
      'Plantas de tratamiento',
    ],
  },
  {
    icon: Cog,
    title: 'Automatismos y Control',
    description: 'Soluciones automatizadas para optimizar procesos',
    items: [
      'Sistemas automatizados',
      'Integración tecnológica',
      'Control de energía reactiva',
      'Procesos industriales',
    ],
  },
  {
    icon: Sun,
    title: 'Energías Renovables',
    description: 'Soluciones limpias y sostenibles para el futuro',
    items: [
      'Paneles solares',
      'Cargadores eléctricos',
      'Soluciones híbridas',
      'Sistemas autosustentables',
    ],
  },
])
</script>

<template>
  <div class="w-full">
    <!-- Hero Section -->
    <section class="bg-gradient-to-r from-blue-700 to-blue-500 text-white py-20">
      <div class="max-w-6xl mx-auto px-4">
        <h1 class="text-5xl md:text-6xl font-bold mb-6">
          Tecno<span class="text-yellow-400">Raíz</span>
        </h1>
        <p class="text-xl md:text-2xl mb-4 font-light">Servicios Integrales</p>
        <p class="text-lg mb-8 text-gray-100 max-w-2xl">
          Especialistas en instalaciones eléctricas de potencia, control, automatismos y energías
          renovables
        </p>
        <div class="flex gap-4">
          <a
            href="#servicios"
            class="bg-yellow-400 text-blue-700 px-8 py-3 rounded-lg font-bold hover:bg-yellow-500 transition-all duration-300 hover:shadow-lg"
          >
            Nuestros Servicios
          </a>
          <a
            href="#contacto"
            class="border-2 border-white text-white px-8 py-3 rounded-lg font-bold hover:bg-white hover:text-blue-700 transition-all duration-300"
          >
            Contáctanos
          </a>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section class="py-16 bg-gray-50">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-4xl font-bold text-blue-700 mb-8 text-center">Sobre TecnoRaíz</h2>
        <div class="grid md:grid-cols-2 gap-8">
          <div class="bg-white p-8 rounded-lg shadow-md">
            <h3 class="text-2xl font-bold text-blue-700 mb-4">Nuestra Historia</h3>
            <p class="text-gray-700 leading-relaxed">
              Tecno Raíz es un emprendimiento joven con raíces firmes en la ingeniería eléctrica.
              Aunque recién comenzamos a operar como empresa, nuestros cimientos están construidos
              sobre más de cinco años de experiencia profesional en el rubro. Fundada por los
              ingenieros Liesvy Delgado y Richard Cruz, nace con el propósito de ofrecer soluciones
              eléctricas modernas, seguras y eficientes.
            </p>
          </div>
          <div class="bg-white p-8 rounded-lg shadow-md">
            <h3 class="text-2xl font-bold text-blue-700 mb-4">Nuestra Misión</h3>
            <p class="text-gray-700 leading-relaxed">
              Brindar soluciones eléctricas de alta calidad, seguras y adaptadas a las necesidades
              actuales, integrando tecnologías limpias y eficientes para contribuir a un futuro más
              sustentable.
            </p>
            <div class="mt-6 pt-6 border-t border-gray-200">
              <h4 class="font-bold text-blue-700 mb-3">¿Por qué elegirnos?</h4>
              <ul class="space-y-2 text-gray-700">
                <li class="flex items-center gap-2">
                  <span class="text-yellow-400">✓</span> Experiencia comprobada en campo
                </li>
                <li class="flex items-center gap-2">
                  <span class="text-yellow-400">✓</span> Atención personalizada y profesional
                </li>
                <li class="flex items-center gap-2">
                  <span class="text-yellow-400">✓</span> Compromiso con la calidad y seguridad
                </li>
                <li class="flex items-center gap-2">
                  <span class="text-yellow-400">✓</span> Enfoque en energías limpias
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Services Section -->
    <section id="servicios" class="py-16 bg-white">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-4xl font-bold text-blue-700 mb-12 text-center">Servicios Integrales</h2>
        <div class="grid md:grid-cols-3 gap-8">
          <div
            v-for="(service, index) in services"
            :key="index"
            class="bg-gradient-to-br from-blue-50 to-blue-100 rounded-lg p-8 shadow-md hover:shadow-lg transition-all duration-300"
          >
            <div class="flex items-center gap-3 mb-4">
              <component :is="service.icon" size="32" class="text-yellow-400" />
              <h3 class="text-xl font-bold text-blue-700">{{ service.title }}</h3>
            </div>
            <p class="text-gray-700 mb-4">{{ service.description }}</p>
            <ul class="space-y-2">
              <li
                v-for="(item, i) in service.items"
                :key="i"
                class="text-gray-600 flex items-center gap-2"
              >
                <span class="text-yellow-400 font-bold">•</span> {{ item }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="bg-blue-700 text-white py-16">
      <div class="max-w-6xl mx-auto px-4 text-center">
        <h2 class="text-4xl font-bold mb-6">¿Listo para transformar tu proyecto?</h2>
        <p class="text-lg mb-8 text-gray-100 max-w-2xl mx-auto">
          Estamos a su disposición para coordinar una reunión, analizar su situación y proponer
          soluciones personalizadas.
        </p>
        <a
          href="#contacto"
          class="inline-block bg-yellow-400 text-blue-700 px-10 py-4 rounded-lg font-bold hover:bg-yellow-500 transition-all duration-300 hover:shadow-lg text-lg"
        >
          Solicitar Cotización
        </a>
      </div>
    </section>
  </div>
</template>

<style scoped></style>
