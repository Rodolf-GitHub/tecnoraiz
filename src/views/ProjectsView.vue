<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const selectedImage = ref<string | null>(null)
const selectedImageIndex = ref(0)
const currentProjectIndex = ref(0)

const projects = ref([
  {
    name: 'Intendencia de Montevideo - Obra PAGRO',
    year: 2026,
    description: 'Reforma de instalación eléctrica y tableros en oficinas y centro de cómputos.',
    images: [
      '/proyectos/pargo/IMG_20260316_170147.jpg',
      '/proyectos/pargo/IMG_20260316_170213.jpg',
      '/proyectos/pargo/IMG_20260316_175636.jpg',
      '/proyectos/pargo/IMG_20260316_175647.jpg',
    ],
  },
  {
    name: 'Edificio Vázquez',
    year: 2025,
    description:
      'Cambio de centralización de medidores, con líneas generales y tablero de servicios.',
    images: ['/proyectos/edificio_vazques/img1.jpeg', '/proyectos/edificio_vazques/img2.jpeg'],
  },
])

const openFullscreen = (image: string, projectIdx: number, imgIdx: number) => {
  selectedImage.value = image
  currentProjectIndex.value = projectIdx
  selectedImageIndex.value = imgIdx
}

const closeFullscreen = () => {
  selectedImage.value = null
}

const goToPrevious = () => {
  const currentProject = projects.value[currentProjectIndex.value]
  if (currentProject && selectedImageIndex.value > 0) {
    selectedImageIndex.value--
    selectedImage.value = currentProject.images[selectedImageIndex.value] || null
  }
}

const goToNext = () => {
  const currentProject = projects.value[currentProjectIndex.value]
  if (currentProject && selectedImageIndex.value < currentProject.images.length - 1) {
    selectedImageIndex.value++
    selectedImage.value = currentProject.images[selectedImageIndex.value] || null
  }
}

const handleKeydown = (e: KeyboardEvent) => {
  if (!selectedImage.value) return
  if (e.key === 'Escape') {
    closeFullscreen()
  } else if (e.key === 'ArrowLeft') {
    goToPrevious()
  } else if (e.key === 'ArrowRight') {
    goToNext()
  }
}

onMounted(() => {
  window.addEventListener('keydown', handleKeydown)
})

onUnmounted(() => {
  window.removeEventListener('keydown', handleKeydown)
})
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

    <!-- Projects Grid -->
    <section class="py-16 bg-white">
      <div class="max-w-6xl mx-auto px-4">
        <div class="grid gap-8">
          <div
            v-for="(project, index) in projects"
            :key="index"
            class="bg-white rounded-lg shadow-lg overflow-hidden border-t-4 border-yellow-400 hover:shadow-xl transition-shadow"
          >
            <!-- Project Header -->
            <div class="bg-gradient-to-r from-blue-700 to-blue-600 text-white p-6">
              <h2 class="text-3xl font-bold">{{ project.name }}</h2>
              <p class="text-blue-100 mt-2">{{ project.description }}</p>
              <div
                class="mt-3 inline-block bg-blue-500 px-3 py-1 rounded-full text-sm font-semibold"
              >
                Año {{ project.year }}
              </div>
            </div>

            <!-- Project Gallery -->
            <div class="p-6">
              <p class="text-sm font-semibold text-gray-700 mb-4">
                {{ project.images.length }} imágenes del proyecto
              </p>
              <div class="grid grid-cols-2 md:grid-cols-4 gap-3">
                <button
                  v-for="(image, imgIndex) in project.images"
                  :key="imgIndex"
                  @click="openFullscreen(image, index, imgIndex)"
                  class="relative overflow-hidden rounded-lg group"
                >
                  <img
                    :src="image"
                    :alt="project.name"
                    class="w-full h-40 object-cover group-hover:scale-110 transition-transform duration-300 cursor-pointer"
                  />
                  <div
                    class="absolute inset-0 bg-black/50 opacity-0 group-hover:opacity-100 transition-opacity flex items-center justify-center"
                  >
                    <span class="text-white text-2xl">🔍</span>
                  </div>
                </button>
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
        <RouterLink
          to="/contacto#formulario"
          class="inline-block bg-yellow-400 text-blue-700 px-10 py-4 rounded-lg font-bold hover:bg-yellow-500 transition-all duration-300 hover:shadow-lg text-lg"
        >
          Solicitar Información
        </RouterLink>
      </div>
    </section>

    <!-- Fullscreen Image Modal -->
    <div
      v-if="selectedImage"
      @click="closeFullscreen"
      class="fixed inset-0 bg-black/90 z-50 flex items-center justify-center p-4"
    >
      <button
        @click.stop="closeFullscreen"
        class="absolute top-4 right-4 text-white hover:text-gray-300 text-3xl z-60"
        aria-label="Cerrar"
      >
        ✕
      </button>

      <!-- Image Container -->
      <div
        @click.stop
        class="relative max-w-4xl max-h-[90vh] w-full h-full flex items-center justify-center"
      >
        <img
          v-if="selectedImage && projects[currentProjectIndex]"
          :src="selectedImage"
          :alt="projects[currentProjectIndex]?.name"
          class="max-w-full max-h-full object-contain"
        />

        <!-- Counter -->
        <div
          v-if="projects[currentProjectIndex]"
          class="absolute bottom-4 left-4 bg-black/50 text-white px-4 py-2 rounded-lg text-sm"
        >
          {{ selectedImageIndex + 1 }} / {{ projects[currentProjectIndex]?.images.length }}
        </div>

        <!-- Navigation Arrows -->
        <button
          v-if="selectedImageIndex > 0"
          @click.stop="goToPrevious"
          class="absolute left-4 top-1/2 transform -translate-y-1/2 bg-white/20 hover:bg-white/40 text-white p-3 rounded-full transition-all"
          aria-label="Imagen anterior"
        >
          ❮
        </button>
        <button
          v-if="
            projects[currentProjectIndex] &&
            selectedImageIndex < projects[currentProjectIndex]!.images.length - 1
          "
          @click.stop="goToNext"
          class="absolute right-4 top-1/2 transform -translate-y-1/2 bg-white/20 hover:bg-white/40 text-white p-3 rounded-full transition-all"
          aria-label="Siguiente imagen"
        >
          ❯
        </button>
      </div>

      <!-- Instructions -->
      <div class="absolute bottom-4 right-4 text-white/70 text-sm text-right">
        <p>Flechas: Anterior/Siguiente</p>
        <p>ESC: Cerrar</p>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
