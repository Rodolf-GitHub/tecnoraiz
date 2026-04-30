<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from 'vue'
import { Zap, Sun, Cog, ChevronLeft, ChevronRight } from 'lucide-vue-next'
import ImageLightbox from '@/components/ImageLightbox.vue'

const currentImageIndex = ref(0)
const currentBgImageIndex = ref(0)
const lightboxIndex = ref<number | null>(null)
let bgImageInterval: ReturnType<typeof setInterval>

const galleryImages = [
  { src: '/carrusel_inicio/instalaciones de paneles solares.jpg', alt: 'Paneles solares' },
  { src: '/carrusel_inicio/imagen parqueo con paneles solares.jpg', alt: 'Parqueo con paneles' },
  { src: '/carrusel_inicio/instalacion de luces interiores.jpg', alt: 'Instalación de luces' },
  { src: '/carrusel_inicio/IMG_20231026_163147.jpg', alt: 'Instalación eléctrica' },
]

const backgroundImages = [
  '/carrusel_inicio/instalaciones de paneles solares.jpg',
  '/carrusel_inicio/imagen parqueo con paneles solares.jpg',
  '/carrusel_inicio/instalacion de luces interiores.jpg',
  '/carrusel_inicio/IMG_20231026_163147.jpg',
]

onMounted(() => {
  bgImageInterval = setInterval(() => {
    currentBgImageIndex.value = (currentBgImageIndex.value + 1) % backgroundImages.length
  }, 5000)
})

onUnmounted(() => {
  clearInterval(bgImageInterval)
})

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

const gallerySources = computed(() => galleryImages.map((g) => g.src))
</script>

<template>
  <div class="w-full">
    <!-- Hero Section with Carousel Background -->
    <section
      class="relative text-white py-32 overflow-hidden"
      :style="{
        backgroundImage: `linear-gradient(rgba(13, 93, 184, 0.7), rgba(47, 126, 216, 0.7)), url('${backgroundImages[currentBgImageIndex]}')`,
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        backgroundAttachment: 'fixed',
        transition: 'background-image 1s ease-in-out',
      }"
    >
      <div class="max-w-6xl mx-auto px-4 relative z-10">
        <h1 class="text-5xl md:text-6xl font-bold mb-6">
          Tecno<span class="text-blue-400">Raíz</span>
        </h1>
        <p class="text-xl md:text-2xl mb-4 font-light">Servicios Integrales</p>
        <p class="text-lg mb-8 text-gray-100 max-w-2xl">
          Especialistas en instalaciones eléctricas de potencia, control, automatismos, iluminación
          interior, terminaciones interiores y energías renovables
        </p>
        <div class="flex gap-4">
          <a
            href="#servicios"
            class="bg-yellow-400 text-blue-700 px-8 py-3 rounded-lg font-bold hover:bg-yellow-500 transition-all duration-300 hover:shadow-lg"
          >
            Nuestros Servicios
          </a>
          <RouterLink
            to="/contacto"
            class="border-2 border-white text-white px-8 py-3 rounded-lg font-bold hover:bg-white hover:text-blue-700 transition-all duration-300"
          >
            Contáctanos
          </RouterLink>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section class="py-16 bg-gray-50">
      <div class="max-w-6xl mx-auto px-4">
        <div class="grid md:grid-cols-2 gap-8">
          <div class="bg-white p-8 rounded-lg shadow-md">
            <h3 class="text-2xl font-bold text-blue-700 mb-4">El origen de TecnoRaíz</h3>
            <p class="text-gray-700 leading-relaxed">
              TecnoRaíz es un emprendimiento joven con raíces firmes en la ingeniería eléctrica.
              Aunque recién comenzamos a operar como empresa, nuestros cimientos se apoyan en más de
              cinco años de experiencia profesional en el rubro. Fundada por los ingenieros Liesvy
              Delgado y Richard Cruz, nace con el propósito de ofrecer soluciones eléctricas
              modernas, seguras y eficientes.
            </p>
          </div>
          <div class="bg-white p-8 rounded-lg shadow-md">
            <h3 class="text-2xl font-bold text-blue-700 mb-4">Nuestra Misión</h3>
            <p class="text-gray-700 leading-relaxed">
              Brindar soluciones integrales en ingeniería eléctrica, automatización y energías
              renovables, combinando innovación, seguridad y eficiencia. Nos comprometemos a
              facilitar la gestión técnica de nuestros clientes mediante un servicio profesional,
              confiable y personalizado, adaptado a cada proyecto y orientado a superar
              expectativas.
            </p>
          </div>
          <div class="bg-white p-8 rounded-lg shadow-md md:col-span-2">
            <h3 class="text-2xl font-bold text-blue-700 mb-4">Visión</h3>
            <p class="text-gray-700 leading-relaxed">
              Ser la empresa líder en Uruguay en servicios eléctricos especializados, reconocida por
              su excelencia técnica, atención directa y capacidad de integrar tecnología avanzada en
              hogares, industrias e instituciones. Aspiramos a transformar la infraestructura
              energética del país con soluciones inteligentes, sostenibles y centradas en el
              cliente.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Services Section -->
    <section id="servicios" class="py-16 bg-white">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-4xl font-bold text-blue-700 mb-12 text-center">Servicios Integrales</h2>

        <!-- Gallery -->
        <div class="mb-16 bg-gray-100 rounded-lg overflow-hidden shadow-lg">
          <div class="relative h-96 bg-black flex items-center justify-center">
            <img
              v-if="galleryImages[currentImageIndex]"
              :src="galleryImages[currentImageIndex]?.src"
              :alt="galleryImages[currentImageIndex]?.alt"
              @click="lightboxIndex = currentImageIndex"
              class="w-full h-full object-cover cursor-zoom-in"
            />
          </div>
          <div class="flex items-center justify-between p-4">
            <button
              @click="
                currentImageIndex =
                  (currentImageIndex - 1 + galleryImages.length) % galleryImages.length
              "
              class="bg-blue-700 text-white p-2 rounded-lg hover:bg-blue-800 transition-colors"
            >
              <ChevronLeft :size="24" />
            </button>
            <div class="flex gap-2">
              <button
                v-for="(img, index) in galleryImages"
                :key="index"
                @click="currentImageIndex = index"
                class="w-12 h-12 rounded-lg overflow-hidden border-2 transition-all"
                :class="currentImageIndex === index ? 'border-yellow-400' : 'border-gray-300'"
              >
                <img :src="img.src" :alt="img.alt" class="w-full h-full object-cover" />
              </button>
            </div>
            <button
              @click="currentImageIndex = (currentImageIndex + 1) % galleryImages.length"
              class="bg-blue-700 text-white p-2 rounded-lg hover:bg-blue-800 transition-colors"
            >
              <ChevronRight :size="24" />
            </button>
          </div>
        </div>

        <div class="grid md:grid-cols-3 gap-8">
          <div
            v-for="(service, index) in services"
            :key="index"
            class="bg-gradient-to-br from-blue-50 to-blue-100 rounded-lg p-8 shadow-md hover:shadow-lg transition-all duration-300"
          >
            <div class="flex items-center gap-3 mb-4">
              <component :is="service.icon" :size="32" class="text-yellow-400" />
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
        <RouterLink
          to="/contacto#formulario"
          class="inline-block bg-yellow-400 text-blue-700 px-10 py-4 rounded-lg font-bold hover:bg-yellow-500 transition-all duration-300 hover:shadow-lg text-lg"
        >
          Cuéntanos tu proyecto
        </RouterLink>
      </div>
    </section>

    <ImageLightbox v-model="lightboxIndex" :images="gallerySources" alt="Servicios Integrales" />
  </div>
</template>

<style scoped></style>
