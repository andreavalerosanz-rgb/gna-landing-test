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
    image: '/image-2.jpg',
    tags: ['Tecnologia']
  },
  {
    id: 2,
    title: 'Lorem ipsum',
    description: "Elit sunt incididunt elit pariatur. Ad anim ea ullamco consectetur dolor excepteur qui velit minim.Ea minim veniam cupidatat in id tempor. Et irure voluptate est eu laborum culpa ullamco laborum qui deserunt id. Minim eiusmod ad Lorem qui incididunt culpa. Veniam culpa officia cupidatat commodo ullamco dolore ut laboris reprehenderit. Proident pariatur ad irure reprehenderit occaecat consequat incididunt mollit consequat. Voluptate exercitation sunt adipisicing dolore sint dolor. Occaecat adipisicing occaecat consequat minim sit exercitation.Exercitation ut voluptate irure ut sit culpa ut aliquip consequat consequat in est. Veniam incididunt dolor ex magna et ullamco laborum proident sit sint mollit. Id sunt Lorem nisi consectetur proident occaecat mollit adipisicing in cupidatat. Voluptate proident duis eiusmod veniam tempor." ,
    image: '/image-1.jpg',
    tags: ['Màrqueting', 'Tecnologia']
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

    <div class="w-full bg-brand-light py-4 sticky top-[7dvh] z-40">
      
      <div class="layout-inner pb-0 flex items-center justify-start gap-5">
        
        <label for="categoryFilter" class="text-gray-900 text-[22px] font-normal whitespace-nowrap">
          Filtrar per
        </label>
        
        <div class="relative w-[280px]">
          <select 
            id="categoryFilter"
            v-model="selectedFilter"
            class="w-full appearance-none bg-white border-none rounded-full px-6 py-3 text-gray-900 text-lg focus:outline-none focus:ring-2 focus:ring-brand-pink shadow-sm cursor-pointer"
          >
            <option v-for="option in filterOptions" :key="option" :value="option">
              {{ option === 'Tots' ? 'Seleccionar' : option }}
            </option>
          </select>
          
          <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-6 text-gray-900">
            <svg class="w-5 h-5 font-light" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.2" d="M19 9l-7 7-7-7"></path>
            </svg>
          </div>
        </div>
        
      </div>
    </div>

    <div class="w-full py-20">
      
      <div class="layout-inner flex flex-col gap-20 lg:gap-28">
        
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
    </div>

  </section>
</template>