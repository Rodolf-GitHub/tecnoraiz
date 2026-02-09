<script setup lang="ts">
import { ref } from 'vue'

const services = ref([
  {
    title: 'Instalaciones Eléctricas de Potencia y Control',
    icon: '⚡',
    subsections: [
      {
        name: 'Sistemas Industriales',
        description:
          'Instalaciones complejas para plantas manufactureras y de procesamiento con cumplimiento de normativas internacionales',
      },
      {
        name: 'Edificios Comerciales y Residenciales',
        description:
          'Soluciones eléctricas adaptadas para edificios modernos con sistemas de distribución eficientes',
      },
      {
        name: 'Plantas de Tratamiento de Aguas Residuales',
        description:
          'Instalaciones especializadas para infraestructura crítica con alta confiabilidad',
      },
    ],
  },
  {
    title: 'Automatismos y Control',
    icon: '🤖',
    subsections: [
      {
        name: 'Diseño e Implementación de Sistemas Automatizados',
        description:
          'Soluciones inteligentes para optimizar procesos industriales y reducir costos operativos',
      },
      {
        name: 'Integración de Tecnologías para Procesos Industriales',
        description:
          'Integración de sistemas modernos con infraestructura existente sin interrupciones',
      },
      {
        name: 'Cálculo y Diseño para Control de Energía Reactiva',
        description: 'Optimización de consumo eléctrico y mejora de factor de potencia',
      },
    ],
  },
  {
    title: 'Energías Renovables',
    icon: '☀️',
    subsections: [
      {
        name: 'Instalación de Paneles Solares Fotovoltaicos',
        description:
          'Sistemas solares personalizados para residencias e industrias con retorno de inversión garantizado',
      },
      {
        name: 'Implementación de Cargadores Eléctricos para Vehículos',
        description:
          'Infraestructura moderna para vehículos eléctricos con tecnología de carga rápida',
      },
      {
        name: 'Soluciones Híbridas y Autosustentables',
        description:
          'Combinación de fuentes de energía renovable para máxima independencia energética',
      },
    ],
  },
])
</script>

<template>
  <div class="w-full">
    <!-- Hero Section -->
    <section class="bg-gradient-to-r from-blue-700 to-blue-500 text-white py-16">
      <div class="max-w-6xl mx-auto px-4">
        <h1 class="text-4xl md:text-5xl font-bold">Servicios Integrales</h1>
        <p class="text-xl mt-4 text-gray-100">
          Soluciones eléctricas modernas, seguras y eficientes
        </p>
      </div>
    </section>

    <!-- Services Detailed -->
    <section class="py-16 bg-gray-50">
      <div class="max-w-6xl mx-auto px-4">
        <div v-for="(service, index) in services" :key="index" class="mb-12">
          <div class="bg-white rounded-lg shadow-md overflow-hidden">
            <div class="bg-gradient-to-r from-blue-700 to-blue-500 p-8 text-white">
              <h2 class="text-3xl font-bold flex items-center gap-4">
                <span class="text-5xl">{{ service.icon }}</span>
                {{ service.title }}
              </h2>
            </div>
            <div class="p-8">
              <div class="grid md:grid-cols-3 gap-6">
                <div
                  v-for="(sub, subIndex) in service.subsections"
                  :key="subIndex"
                  class="bg-blue-50 rounded-lg p-6 border-l-4 border-yellow-400"
                >
                  <h3 class="text-xl font-bold text-blue-700 mb-3">{{ sub.name }}</h3>
                  <p class="text-gray-700">{{ sub.description }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Call to Action -->
    <section class="bg-blue-700 text-white py-16">
      <div class="max-w-6xl mx-auto px-4 text-center">
        <h2 class="text-4xl font-bold mb-6">¿Necesitas una solución personalizada?</h2>
        <p class="text-xl mb-8 text-gray-100 max-w-2xl mx-auto">
          Contacta con nuestro equipo de ingenieros para analizar tu proyecto y proponer la mejor
          solución
        </p>
        <a
          href="/#contacto"
          class="inline-block bg-yellow-400 text-blue-700 px-10 py-4 rounded-lg font-bold hover:bg-yellow-500 transition-all duration-300 hover:shadow-lg text-lg"
        >
          Solicitar Presupuesto
        </a>
      </div>
    </section>
  </div>
</template>

<style scoped></style>
