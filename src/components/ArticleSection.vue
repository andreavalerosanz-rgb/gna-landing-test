<script setup>
import { ref, computed } from 'vue'
import ArticleCard from './ArticleCard.vue'


// El filtro seleccionado por el usuario ('Tots' por defecto para mostrar todos)
const selectedFilter = ref('Tots')

// Opciones del selector
const filterOptions = ['Tots', 'Tecnologia', 'Màrqueting']

// Array mock data
const projects = ref([
  {
    id: 1,
    title: 'Lorem ipsum',
    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam rhoncus, velit id viverra fermentum, mauris odio maximus augue, ac pretium diam nunc non lacus. Suspendisse mattis pellentesque velit, a vestibulum felis condimentum et.',
    image: '/image-1.jpg',
    tags: ['Tecnologia']
  },
  {
    id: 2,
    title: 'Lorem ipsum',
    description: 'Pellentesque hendrerit sit amet mauris vel dapibus. In felis diam, ornare vel iaculis et, egestas sit amet dolor. Nulla nec cursus dui. Nulla vulputate dolor et nunc feugiat tempus.',
    image: '/image-2.jpg',
    tags: ['Màrqueting', 'Tecnologia']
  },
  {
    id: 3,
    title: 'Lorem ipsum',
    description: 'Nam ac ante ac felis molestie dictum at et risus. Quisque sagittis dignissim accumsan. Aliquam mattis volutpat condimentum. Interdum et malesuada fames ac ante ipsum primis in faucibus.',
    image: '/image-1.jpg',
    tags: ['Màrqueting']
  }
])



// Filtramos los proyectos sin modificar el array original
const filteredProjects = computed(() => {
  // Si el filtro es "Tots", devolvemos el array entero
  if (selectedFilter.value === 'Tots') {
    return projects.value
  }
  // Si no, devolvemos solo los que incluyan el tag seleccionado
  return projects.value.filter(project => project.tags.includes(selectedFilter.value))
})
</script>

<template>
  <section id="ofertas" class="w-full bg-white">
    
    <div class="w-full bg-brand-light py-6">
      <div class="max-w-[950px] mx-auto px-6 md:px-12 flex items-center gap-4">
        <label for="categoryFilter" class="text-brand-dark text-lg font-medium">
          Filtrar per
        </label>
        <div class="relative w-64">
            <!--cuando cambie el selected filter se auto triggerea la funcion del filtro
             si no cambia el filtro pero se reprinta el componente no triggerea otra vez y ahorramos rendimiento -->
          <select 
            id="categoryFilter"
            v-model="selectedFilter"
            class="w-full appearance-none bg-white border-none rounded-full px-6 py-2.5 text-brand-dark focus:outline-none focus:ring-2 focus:ring-brand-pink shadow-sm cursor-pointer"
          >
            <option v-for="option in filterOptions" :key="option" :value="option">
              {{ option === 'Tots' ? 'Seleccionar' : option }}
            </option>
          </select>
          
          <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-5 text-gray-500">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19 9l-7 7-7-7"></path>
            </svg>
          </div>
        </div>
      </div>
    </div>

    <div class="max-w-[1200px] mx-auto px-6 md:px-12 py-16 md:py-24 flex flex-col gap-20 md:gap-32">
      
      <ArticleCard 
        v-for="(project, index) in filteredProjects" 
        :key="project.id"
        :title="project.title"
        :description="project.description"
        :image="project.image"
        :tags="project.tags"
        :is-reversed="index % 2 !== 0"
      />
      
      <div v-if="filteredProjects.length === 0" class="text-center text-gray-500 py-10">
        No hi ha projectes amb aquesta categoria.
      </div>

    </div>

  </section>
</template>