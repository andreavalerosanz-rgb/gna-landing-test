<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const isMenuOpen = ref(false)
const sentinel = ref(null) // creamos el sentinel
let observer = null

const navClasses = computed(() => {
  return (isScrolled.value || isMenuOpen.value)
    ? 'bg-brand-pink shadow-md py-3'
    : 'bg-transparent py-5'
})

const logoSolutionsClass = computed(() => {
  return (isScrolled.value || isMenuOpen.value)
    ? 'text-white'
    : 'text-brand-pink'
})

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}

onMounted(() => {
  // Creamos el observador
  observer = new IntersectionObserver(([entry]) => {
    // si el sentinel está visible significa que no hemos scrolleado
    isScrolled.value = !entry.isIntersecting
  }, { 
    // customization: ajustar margen 
    rootMargin: '0px',
    threshold: 0 
  })

  if (sentinel.value) {
    observer.observe(sentinel.value)
  }
})

onUnmounted(() => {
  // Limpieza: desconectar el observador
  if (observer) {
    observer.disconnect()
  }
})
</script>

<template>
  <header 
    class="relative w-full h-dvh bg-cover bg-center bg-no-repeat" 
    style="background-image: url('/girona.jpg');"
  >
    <div ref="sentinel" class="absolute top-0 left-0 w-full h-1 pointer-events-none opacity-0"></div>
<!-- darken porque sino se veia muy saturado-->
    <div class="absolute inset-0 bg-black/40"></div>

    <nav :class="['fixed top-0 left-0 w-full z-50 transition-all duration-300 text-white', navClasses]">
      
      <div class="px-6 md:px-16 lg:px-24 flex items-center justify-between">
      <!-- logo recreado porque la resolución de la imagen era muy baja-->  
        <div class="flex flex-col relative z-50">
          <span class="text-2xl tracking-tight">
            <span class="font-light text-white">GNAHotel</span><span :class="['font-bold transition-colors', logoSolutionsClass]">Solutions</span>
          </span>
          <span class="text-[0.8rem]  mt-0.5 text-white">
            strategy & e-technology for success
          </span>
        </div>
    <!-- menu con anclas porque es un onepage, con un collapse para moviles-->
        <button 
          @click="toggleMenu" 
          class="md:hidden relative z-50 p-2 focus:outline-none"
          aria-label="Toggle Menu"
        >
          <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
            <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
          </svg>
        </button>
        
        <ul class="hidden md:flex items-center gap-8 text-sm font-medium">
          <li>
            <a href="#hotel" 
               :class="['transition-colors', isScrolled ? 'hover:text-brand-dark' : 'hover:text-brand-pink']">
              Hotel
            </a>
          </li>
          <li>
            <a href="#ofertas" 
               :class="['transition-colors', isScrolled ? 'hover:text-brand-dark' : 'hover:text-brand-pink']">
              Ofertas
            </a>
          </li>
          <li>
            <a href="#reservar" 
               :class="[
                 'px-7 py-2 rounded-full border transition-all duration-300 border-white hover:bg-white',
                 isScrolled ? 'hover:text-brand-pink' : 'hover:text-brand-dark'
               ]"
            >
              Reservar
            </a>
          </li>
        </ul>
      </div>

      <div 
        v-show="isMenuOpen" 
        class="md:hidden absolute top-full left-0 w-full bg-brand-pink shadow-lg border-t border-white/20 transition-all duration-300"
      >
        <ul class="flex flex-col px-6 py-6 gap-6 text-base font-medium">
          <li>
            <a href="#hotel" @click="closeMenu" class="block hover:text-brand-dark transition-colors">Hotel</a>
          </li>
          <li>
            <a href="#ofertas" @click="closeMenu" class="block hover:text-brand-dark transition-colors">Ofertas</a>
          </li>
          <li class="pt-2">
            <a href="#reservar" @click="closeMenu" class="inline-block px-8 py-2.5 rounded-full border border-white hover:bg-white hover:text-brand-pink transition-colors">
              Reservar
            </a>
          </li>
        </ul>
      </div>
    </nav>
<!-- TITULO-->
    <div class="relative z-10 flex h-full items-end justify-center px-4 pb-28 md:pb-40">
      <h1 class="text-5xl md:text-6xl lg:text-[5.5rem] font-extrabold text-white uppercase tracking-[0.15em] drop-shadow-2xl text-center">
        GNA Hotel Solutions
      </h1>
    </div>

  </header>
</template>