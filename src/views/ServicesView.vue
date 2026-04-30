<script setup lang="ts">
import { ref } from 'vue'

const services = ref([
  {
    title: 'Instalaciones Eléctricas de Potencia e Iluminación',
    icon: '⚡',
    image: '/servicios/Instalacion Electrica Potencia e iluminacion/IMG_20240220_160412.jpg',
    gallery: [
      '/servicios/Instalacion Electrica Potencia e iluminacion/IMG-20250326-WA0005.jpg',
      '/servicios/Instalacion Electrica Potencia e iluminacion/IMG-20250326-WA0007.jpg',
      '/servicios/Instalacion Electrica Potencia e iluminacion/IMG-20250326-WA0008.jpg',
      '/servicios/Instalacion Electrica Potencia e iluminacion/IMG_20250224_174317.jpg',
      '/servicios/Instalacion Electrica Potencia e iluminacion/IMG_20250318_182343.jpg',
    ],
    subsections: [
      {
        name: 'Montaje de sistemas industriales',
        description:
          'Ejecución de instalaciones eléctricas para plantas industriales con cumplimiento normativo y altos estándares de seguridad.',
      },
      {
        name: 'Instalaciones de potencia e iluminación en edificios comerciales y residenciales',
        description:
          'Soluciones eléctricas integrales adaptadas a edificios modernos, optimizando consumo y confort.',
      },
      {
        name: 'Cálculo y diseño para el control de energía reactiva',
        description:
          'Mejora del factor de potencia para reducir costos energéticos y prevenir penalizaciones.',
      },
      {
        name: 'Cálculo, diseño e instalación de sistemas de puesta a tierra y protección contra descargas atmosféricas',
        description:
          'Protección integral de instalaciones, equipos y personas mediante sistemas certificados.',
      },
    ],
  },
  {
    title: 'Automatismos y Control',
    icon: '🤖',
    image: '/servicios/Automatismo y control/IMG_20231026_162859.jpg',
    gallery: [
      '/servicios/Automatismo y control/IMG_20231121_100443.jpg',
      '/servicios/Automatismo y control/IMG_20231208_123156.jpg',
      '/servicios/Automatismo y control/IMG_20240320_110224.jpg',
    ],
    subsections: [
      {
        name: 'Diseño e implementación de sistemas automatizados',
        description:
          'Soluciones inteligentes para optimizar procesos industriales y reducir costos operativos.',
      },
      {
        name: 'Programación y control de pozos de bombeo y planta de tratamiento',
        description:
          'Automatización de sistemas hidráulicos críticos garantizando continuidad y eficiencia operativa.',
      },
      {
        name: 'Comunicación, programación e implantación de sistemas PLC y SCADA',
        description:
          'Supervisión y control centralizado de procesos con tecnologías industriales de última generación.',
      },
    ],
  },
  {
    title: 'Energías Renovables',
    icon: '☀️',
    image: '/servicios/energias renobables/img1.jpg',
    gallery: [
      '/servicios/energias renobables/img2.jpg',
      '/servicios/energias renobables/IMG_1262.jpg',
      '/servicios/energias renobables/liesvi 4.jpg.jpeg',
      '/servicios/energias renobables/R.jpeg',
    ],
    subsections: [
      {
        name: 'Instalación de paneles solares fotovoltaicos',
        description:
          'Sistemas solares personalizados para residencias e industrias con retorno de inversión garantizado.',
      },
      {
        name: 'Instalación de cargadores para vehículos eléctricos',
        description:
          'Infraestructura moderna de carga para vehículos eléctricos con tecnología de carga rápida.',
      },
      {
        name: 'Alquiler y venta de plantas solares móviles',
        description:
          'Soluciones energéticas portátiles para obras, eventos y ubicaciones sin acceso a la red eléctrica.',
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
            <div class="flex flex-col">
              <!-- Image (always above) -->
              <div v-if="service.image" class="overflow-hidden bg-gray-100 w-full">
                <img
                  :src="service.image"
                  :alt="service.title"
                  class="w-full h-64 md:h-96 object-cover"
                />
              </div>
              <!-- Content -->
              <div>
                <div class="bg-gradient-to-r from-blue-700 to-blue-500 p-8 text-white">
                  <h2 class="text-3xl font-bold flex items-center gap-4">
                    <span class="text-5xl">{{ service.icon }}</span>
                    {{ service.title }}
                  </h2>
                </div>
                <div class="p-8">
                  <div class="grid md:grid-cols-1 gap-6">
                    <div
                      v-for="(sub, subIndex) in service.subsections"
                      :key="subIndex"
                      class="bg-blue-50 rounded-lg p-6 border-l-4 border-yellow-400"
                    >
                      <h3 class="text-xl font-bold text-blue-700 mb-3">{{ sub.name }}</h3>
                      <p class="text-gray-700">{{ sub.description }}</p>
                    </div>
                  </div>
                  <div
                    v-if="service.gallery && service.gallery.length"
                    class="mt-8 grid grid-cols-2 md:grid-cols-4 gap-3"
                  >
                    <img
                      v-for="(img, i) in service.gallery"
                      :key="i"
                      :src="img"
                      :alt="service.title"
                      class="w-full h-32 object-cover rounded-lg shadow hover:scale-105 transition-transform"
                    />
                  </div>
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
        <RouterLink
          to="/contacto#formulario"
          class="inline-block bg-yellow-400 text-blue-700 px-10 py-4 rounded-lg font-bold hover:bg-yellow-500 transition-all duration-300 hover:shadow-lg text-lg"
        >
          Cuéntanos tu proyecto
        </RouterLink>
      </div>
    </section>
  </div>
</template>

<style scoped></style>
