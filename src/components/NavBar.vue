<script setup lang="ts">
import { ref } from 'vue'
import { RouterLink } from 'vue-router'
import { Menu, X, Phone, Mail } from 'lucide-vue-next'

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}
</script>

<template>
  <!-- Info Bar -->
  <div class="bg-blue-900 text-white py-2 px-4 text-xs">
    <div
      class="max-w-6xl mx-auto flex flex-col md:flex-row md:justify-between md:items-center gap-2"
    >
      <div class="flex flex-col md:flex-row gap-4 md:gap-6">
        <div class="flex items-center gap-2">
          <span class="font-semibold">Ing. Richard Cruz</span>
          <Phone size="14" class="text-yellow-400" />
          <span class="text-yellow-400 font-bold">094774616</span>
        </div>
        <div class="flex items-center gap-2">
          <span class="font-semibold">Ing. Liesvy Delgado</span>
          <Phone size="14" class="text-yellow-400" />
          <span class="text-yellow-400 font-bold">094840059</span>
        </div>
      </div>
      <div class="flex items-center gap-2">
        <Mail size="14" class="text-yellow-400" />
        <a href="mailto:tecnoraizadm@gmail.com" class="text-yellow-400 font-bold hover:underline"
          >tecnoraizadm@gmail.com</a
        >
      </div>
    </div>
  </div>

  <!-- Navbar -->
  <nav class="bg-gradient-to-r from-blue-700 to-blue-500 sticky top-8 z-50 shadow-lg">
    <div class="max-w-6xl mx-auto px-4 py-3 flex justify-between items-center">
      <!-- Logo -->
      <div class="flex items-center gap-3">
        <div
          class="bg-yellow-400 p-2 rounded-lg shadow-md hover:shadow-lg hover:translate-y-[-2px] transition-all duration-300"
        >
          <img src="@/assets/mini_logo.png" alt="TecnoRaiz" class="h-10 w-auto" />
        </div>
        <RouterLink
          to="/"
          class="bg-white rounded-lg px-4 py-2 hover:shadow-lg hover:translate-y-[-2px] transition-all duration-300"
          @click="closeMenu"
        >
          <div class="text-sm">
            <p class="text-blue-700 font-bold text-lg">TecnoRaíz</p>
            <p class="text-yellow-400 font-semibold text-xs tracking-wider">Servicios Integrales</p>
          </div>
        </RouterLink>
      </div>

      <!-- Menu Toggle Button (Mobile) -->
      <button
        class="md:hidden text-white hover:text-yellow-400 transition-colors"
        @click="toggleMenu"
      >
        <Menu v-if="!isMenuOpen" size="28" />
        <X v-else size="28" />
      </button>

      <!-- Navigation Menu -->
      <ul
        class="absolute md:static top-full left-0 right-0 md:flex list-none m-0 p-0 gap-1 items-center"
        :class="[
          'md:bg-transparent',
          isMenuOpen ? 'max-h-96 bg-blue-700 shadow-lg' : 'max-h-0 overflow-hidden md:max-h-none',
          'transition-all duration-300',
        ]"
      >
        <li>
          <RouterLink
            to="/"
            class="block px-5 py-3 text-white font-medium rounded-md transition-all duration-300 hover:bg-white hover:bg-opacity-10 hover:text-yellow-400 relative group"
            @click="closeMenu"
          >
            Inicio
            <span
              class="absolute bottom-0 left-0 w-0 h-1 bg-yellow-400 rounded group-hover:w-full transition-all duration-300"
            ></span>
          </RouterLink>
        </li>
        <li>
          <RouterLink
            to="/about"
            class="block px-5 py-3 text-white font-medium rounded-md transition-all duration-300 hover:bg-white hover:bg-opacity-10 hover:text-yellow-400 relative group"
            @click="closeMenu"
          >
            Sobre Nosotros
            <span
              class="absolute bottom-0 left-0 w-0 h-1 bg-yellow-400 rounded group-hover:w-full transition-all duration-300"
            ></span>
          </RouterLink>
        </li>
        <li>
          <a
            href="#servicios"
            class="block px-5 py-3 text-white font-medium rounded-md transition-all duration-300 hover:bg-white hover:bg-opacity-10 hover:text-yellow-400 relative group"
            @click="closeMenu"
          >
            Servicios
            <span
              class="absolute bottom-0 left-0 w-0 h-1 bg-yellow-400 rounded group-hover:w-full transition-all duration-300"
            ></span>
          </a>
        </li>
        <li>
          <a
            href="#contacto"
            class="block px-5 py-3 text-white font-medium rounded-md transition-all duration-300 hover:bg-white hover:bg-opacity-10 hover:text-yellow-400 relative group"
            @click="closeMenu"
          >
            Contacto
            <span
              class="absolute bottom-0 left-0 w-0 h-1 bg-yellow-400 rounded group-hover:w-full transition-all duration-300"
            ></span>
          </a>
        </li>
        <li>
          <button
            class="block w-full md:w-auto px-6 py-3 mx-3 my-1 md:my-0 bg-yellow-400 text-blue-700 font-bold rounded-lg hover:bg-yellow-500 transition-all duration-300 hover:shadow-lg hover:translate-y-[-2px] active:translate-y-0"
            @click="closeMenu"
          >
            Obtener Cotización
          </button>
        </li>
      </ul>
    </div>
  </nav>
</template>
