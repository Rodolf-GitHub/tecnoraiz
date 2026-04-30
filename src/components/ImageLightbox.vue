<script setup lang="ts">
import { computed, onMounted, onUnmounted, watch } from 'vue'

const props = defineProps<{
  images: string[]
  modelValue: number | null
  alt?: string
}>()

const emit = defineEmits<{
  (e: 'update:modelValue', value: number | null): void
}>()

const currentIndex = computed(() => props.modelValue)
const currentImage = computed(() =>
  currentIndex.value !== null ? props.images[currentIndex.value] : null,
)

const close = () => emit('update:modelValue', null)

const goToPrevious = () => {
  if (currentIndex.value !== null && currentIndex.value > 0) {
    emit('update:modelValue', currentIndex.value - 1)
  }
}

const goToNext = () => {
  if (currentIndex.value !== null && currentIndex.value < props.images.length - 1) {
    emit('update:modelValue', currentIndex.value + 1)
  }
}

const handleKeydown = (e: KeyboardEvent) => {
  if (currentIndex.value === null) return
  if (e.key === 'Escape') close()
  else if (e.key === 'ArrowLeft') goToPrevious()
  else if (e.key === 'ArrowRight') goToNext()
}

onMounted(() => window.addEventListener('keydown', handleKeydown))
onUnmounted(() => window.removeEventListener('keydown', handleKeydown))

watch(
  () => props.modelValue,
  (v) => {
    if (typeof document !== 'undefined') {
      document.body.style.overflow = v !== null ? 'hidden' : ''
    }
  },
)
</script>

<template>
  <div
    v-if="currentImage !== null && currentIndex !== null"
    @click="close"
    class="fixed inset-0 bg-black/90 z-50 flex items-center justify-center p-4"
  >
    <button
      @click.stop="close"
      class="absolute top-4 right-4 text-white hover:text-gray-300 text-3xl z-60"
      aria-label="Cerrar"
    >
      ✕
    </button>

    <div
      @click.stop
      class="relative max-w-5xl max-h-[90vh] w-full h-full flex items-center justify-center"
    >
      <img
        :src="currentImage"
        :alt="alt || 'Imagen'"
        class="max-w-full max-h-full object-contain"
      />

      <div
        v-if="images.length > 1"
        class="absolute bottom-4 left-4 bg-black/50 text-white px-4 py-2 rounded-lg text-sm"
      >
        {{ currentIndex + 1 }} / {{ images.length }}
      </div>

      <button
        v-if="currentIndex > 0"
        @click.stop="goToPrevious"
        class="absolute left-4 top-1/2 transform -translate-y-1/2 bg-white/20 hover:bg-white/40 text-white p-3 rounded-full transition-all"
        aria-label="Imagen anterior"
      >
        ❮
      </button>
      <button
        v-if="currentIndex < images.length - 1"
        @click.stop="goToNext"
        class="absolute right-4 top-1/2 transform -translate-y-1/2 bg-white/20 hover:bg-white/40 text-white p-3 rounded-full transition-all"
        aria-label="Siguiente imagen"
      >
        ❯
      </button>
    </div>

    <div
      v-if="images.length > 1"
      class="absolute bottom-4 right-4 text-white/70 text-sm text-right"
    >
      <p>Flechas: Anterior/Siguiente</p>
      <p>ESC: Cerrar</p>
    </div>
  </div>
</template>
