<script setup>
defineProps({
  title: {
    type: String,
    required: true
  },
  description: {
    type: String,
    required: true
  },
  image: {
    type: String,
    required: true
  },
  tags: {
    type: Array,
    required: true
  },
  // Si es true, la imagen se pone a la derecha en escritorio
  isReversed: {
    type: Boolean,
    default: false
  }
})
</script>

<template>
  <article 
    :class="[
      'flex flex-col gap-8 md:gap-12 lg:gap-16 items-center w-full',
      isReversed ? 'md:flex-row-reverse' : 'md:flex-row'
    ]"
  >
    
    <div class="w-full md:w-1/2">
      <img 
        :src="image" 
        :alt="title" 
        class="w-full rounded-2xl md:rounded-[2rem] object-cover shadow-lg aspect-[4/3] md:aspect-auto md:h-72 lg:h-[22rem]" 
      />
    </div>

    <div class="w-full md:w-1/2 flex flex-col justify-center text-left">
      
      <div class="flex flex-wrap gap-2 mb-5">
        <span 
          v-for="tag in tags" 
          :key="tag" 
          class="px-4 py-1 text-[0.65rem] font-semibold text-white bg-brand-pink rounded-full"
        >
          {{ tag }}
        </span>
      </div>

      <h3 class="text-xl md:text-2xl font-bold text-brand-dark mb-4">
        {{ title }}
      </h3>

      <p class="text-[0.95rem] text-brand-dark leading-relaxed mb-6">
        {{ description }}
      </p>

      <a href="#" class="text-brand-pink font-medium text-sm hover:underline w-max">
        Més informació
      </a>
      
    </div>
    
  </article>
</template>