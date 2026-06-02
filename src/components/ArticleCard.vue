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
      'flex flex-col lg:items-center justify-between w-full gap-10 lg:gap-0',
      isReversed ? 'lg:flex-row-reverse' : 'lg:flex-row'
    ]"
  >
    
    <div class="w-full lg:w-[35%]">
      <img 
        :src="image" 
        :alt="title" 
        class="w-full rounded-[1.5rem] md:rounded-[2rem] object-cover shadow-md aspect-[4/3]" 
      />
    </div>

    <div class="w-full lg:w-[60%] flex flex-col justify-center items-start text-left py-4">
      
      <div class="flex flex-wrap gap-3 mb-6 w-full">
        <span 
          v-for="tag in tags" 
          :key="tag" 
          class="px-5 py-3 text-[1.7dvh] tracking-wide text-white bg-brand-pink rounded-3xl leading-none inline-flex items-center justify-center"
        >
          {{ tag }}
        </span>
      </div>

      <h3 class="text-2xl md:text-[28px] text-black font-bold mb-5 leading-tight w-full">
        {{ title }}
      </h3>

      <p class="text-[1.7dvh] leading-relaxed text-black  mb-6 w-full">
        {{ description }}
      </p>

      <a href="#" class="text-brand-pink font-medium text-[1.7dvh] underline hover:no-underline w-max">
        Més informació
      </a>
      
    </div>
    
  </article>
</template>