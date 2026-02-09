<script setup lang="ts">
import { ref } from 'vue'

const projectsLiesvy = ref([
  {
    year: 2023,
    description:
      'Instalación eléctrica de potencia y control de Planta Efluentes Parque de las Ciencias',
    amount: '$6.400.000,00',
    client: 'CUJO SA',
    contact: 'Ing. Rodolfo Ferreira',
    phone: '47334360',
  },
  {
    year: 2023,
    description:
      'Instalación eléctrica de potencia y control de pozo de Bombeo Aparicio Sarabia, para OSE Las Piedras',
    amount: '$1.387.506,00',
    client: 'INSACO SA',
    contact: 'Ing. Nadia Sandez',
    phone: '097908344',
  },
  {
    year: 2023,
    description:
      'Instalación eléctrica de potencia (Incluida Subestación) Para la Nueva UCUDAL San Jose ubicada en AV. 8 de Octubre',
    amount: '$14.490.695,03',
    client: 'CIEMSA-SURESTE',
    contact: 'Arq. Martin Villar / Arq. Alfonso Viera',
    phone: '096806229 / 099096669',
  },
  {
    year: 2023,
    description:
      'Instalación Eléctrica y cambio de Centralización de medidores en el edificio ubicado en 18 de julio 2020, tras el incendio de la galería entrevero',
    amount: '$410.972,00',
    client: 'Adm. Edif 18 de Julio 2020',
    contact: 'Adriana Frattini',
    phone: '099207400',
  },
  {
    year: 2024,
    description: 'Obras de distribución UTE Canelones las Piedras',
    amount: '$3.500.000,00',
    client: 'BERKES SA',
    contact: "Ing. Héctor D'Helia",
    phone: '092456087',
  },
  {
    year: 2024,
    description:
      'Instalación eléctrica de Potencia Para el Obrador destinado a la Ampliación y dragado de la terminal del Puerto de Montevideo',
    amount: '$2.654.918,57',
    client: 'STILER-JEAN DE NUL',
    contact: 'Ing. Franco Crotti',
    phone: '091794034',
  },
  {
    year: 2024,
    description:
      'Instalación eléctrica de Potencia para PEPSICO SALES en Zona Franca Colonia de Sacramento',
    amount: '$9.839.822,45',
    client: 'CIEMSA SA',
    contact: 'Ing. Verónica Aguilar',
    phone: '099301326',
  },
  {
    year: 2024,
    description:
      'Instalación Eléctrica de Potencia para la Nueva ORT ubicada en Luis de la Torre 919',
    amount: '$10.301.874,21',
    client: 'CIEMSA-SURESTE',
    contact: 'Arq. Alberto Peverelli',
    phone: '099112705',
  },
])

const projectsRichard = ref([
  {
    year: 2023,
    description: 'Instalación eléctrica de potencia de las oficinas de Sebamar',
    client: 'Sebamar',
    contact: 'Ing. Jonathan Barbosa',
    phone: '092155581',
    company: 'Empresa Constructora ARCA',
  },
  {
    year: 2024,
    description:
      'Instalación eléctrica de potencia y cámaras de seguridad de las oficinas del Comunal Z10',
    client: 'Comunal Z10',
    contact: 'Arq. Enrique Homero',
    phone: '099191765',
    company: 'Intendencia de Montevideo',
  },
  {
    year: 2024,
    description: 'Instalación eléctrica de potencia del Edificio de 60 apt Altos del Cordón',
    client: 'Altos del Cordón',
    contact: 'Arq. Yamila',
    phone: '099727159',
    company: 'Empresa Constructora CSA',
  },
  {
    year: 2024,
    description: 'Edificio de 80 apt',
    client: 'Edif Mercedes',
    contact: 'Arq. Guillermo',
    phone: '094154106',
    company: 'Empresa Constructora CSA',
  },
  {
    year: 2025,
    description:
      'Rehabilitación de la Instalación eléctrica de potencia de las oficinas y locales comerciales del Axion',
    client: 'Axion Libertad',
    contact: 'Arq. Javier Pérez',
    phone: '099221701',
    company: 'Axion',
  },
  {
    year: 2025,
    description:
      'Rehabilitación de la Instalación eléctrica de potencia de las oficinas y locales comerciales del Axion',
    client: 'Axion Santa Lucia',
    contact: 'Arq. Javier Pérez',
    phone: '099221701',
    company: 'Axion',
  },
])
</script>

<template>
  <div class="w-full">
    <!-- Hero Section -->
    <section class="bg-gradient-to-r from-blue-700 to-blue-500 text-white py-16">
      <div class="max-w-6xl mx-auto px-4">
        <h1 class="text-4xl md:text-5xl font-bold">Nuestros Proyectos</h1>
        <p class="text-xl mt-4 text-gray-100">Experiencia comprobada en el mercado</p>
      </div>
    </section>

    <!-- Liesvy Projects -->
    <section class="py-16 bg-white">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-3xl font-bold text-blue-700 mb-2">Referencias Profesionales</h2>
        <p class="text-xl text-yellow-400 font-bold mb-8">Ing. Liesvy Delgado - 094840059</p>

        <div class="overflow-x-auto">
          <table class="w-full border-collapse">
            <thead>
              <tr class="bg-blue-700 text-white">
                <th class="border border-gray-300 p-3 text-left">Año</th>
                <th class="border border-gray-300 p-3 text-left">Descripción</th>
                <th class="border border-gray-300 p-3 text-left">Monto</th>
                <th class="border border-gray-300 p-3 text-left">Cliente</th>
                <th class="border border-gray-300 p-3 text-left">Contacto</th>
              </tr>
            </thead>
            <tbody>
              <tr
                v-for="(project, index) in projectsLiesvy"
                :key="index"
                class="hover:bg-blue-50 transition-colors"
              >
                <td class="border border-gray-300 p-3 font-bold text-blue-700">
                  {{ project.year }}
                </td>
                <td class="border border-gray-300 p-3">{{ project.description }}</td>
                <td class="border border-gray-300 p-3 font-bold text-yellow-600">
                  {{ project.amount }}
                </td>
                <td class="border border-gray-300 p-3">{{ project.client }}</td>
                <td class="border border-gray-300 p-3">
                  <div class="text-sm">
                    <p class="font-semibold">{{ project.contact }}</p>
                    <p class="text-gray-600">{{ project.phone }}</p>
                  </div>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- Richard Projects -->
    <section class="py-16 bg-gray-50">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-3xl font-bold text-blue-700 mb-2">Referencias Profesionales</h2>
        <p class="text-xl text-yellow-400 font-bold mb-8">Ing. Richard Cruz - 094774616</p>

        <div class="grid gap-6">
          <div
            v-for="(project, index) in projectsRichard"
            :key="index"
            class="bg-white rounded-lg shadow-md p-6 border-l-4 border-yellow-400"
          >
            <div class="flex flex-col md:flex-row md:justify-between md:items-start gap-4">
              <div class="flex-1">
                <div class="flex items-center gap-3 mb-2">
                  <span
                    class="bg-blue-700 text-white rounded-full w-12 h-12 flex items-center justify-center font-bold"
                    >{{ project.year }}</span
                  >
                  <h3 class="text-lg font-bold text-blue-700">{{ project.description }}</h3>
                </div>
                <p class="text-gray-700 ml-15">
                  <span class="font-semibold">Cliente:</span> {{ project.client }}
                </p>
              </div>
              <div class="bg-blue-50 p-4 rounded-lg text-right">
                <p class="text-sm font-semibold text-blue-700">{{ project.contact }}</p>
                <p class="text-yellow-600 font-bold">{{ project.phone }}</p>
                <p class="text-xs text-gray-600 mt-2">{{ project.company }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Call to Action -->
    <section class="bg-blue-700 text-white py-16">
      <div class="max-w-6xl mx-auto px-4 text-center">
        <h2 class="text-4xl font-bold mb-6">¿Tu proyecto es el siguiente?</h2>
        <p class="text-xl mb-8 text-gray-100">
          Nos encantaría trabajar con vos. Contacta con nosotros para una consulta gratuita.
        </p>
        <a
          href="/#contacto"
          class="inline-block bg-yellow-400 text-blue-700 px-10 py-4 rounded-lg font-bold hover:bg-yellow-500 transition-all duration-300 hover:shadow-lg text-lg"
        >
          Solicitar Información
        </a>
      </div>
    </section>
  </div>
</template>

<style scoped></style>
