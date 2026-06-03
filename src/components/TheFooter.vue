<template>
  <footer class="w-full bg-brand-light pt-12 md:pt-16 lg:pt-20 pb-10">

    <div class="layout-outer flex flex-col md:flex-row md:items-start gap-10 md:gap-0">

      <!-- LEFT: logo -->
      <div class="shrink-0">
        <img
          src="/logo-gnahs.png"
          alt="GNA Hotel Solutions"
          class="w-[220px] sm:w-[280px] lg:w-[420px] object-contain"
        />
      </div>

      <!-- RIGHT: on mobile full width, on lg the existing layout -->
      <div class="flex flex-col gap-8 lg:gap-12 w-full md:ml-auto md:w-auto lg:pr-40">

        <div class="flex flex-row gap-8 sm:gap-12 lg:gap-37 justify-between md:justify-start">
          <ul class="flex flex-col gap-4 lg:gap-5 text-[1.5dvh] lg:text-[1.7dvh] text-gray-900">
            <li><a href="#" class="hover:text-brand-pink transition-colors">Contacte</a></li>
            <li><a href="#" class="hover:text-brand-pink transition-colors">Newsletter</a></li>
            <li><a href="#" class="hover:text-brand-pink transition-colors">Treballa amb nosaltres</a></li>
          </ul>
          <ul class="flex flex-col gap-4 lg:gap-5 text-[1.5dvh] lg:text-[1.7dvh] text-gray-900">
            <li><a href="#" class="hover:text-brand-pink transition-colors">Política de cookies</a></li>
            <li><a href="#" class="hover:text-brand-pink transition-colors">Política de privacitat</a></li>
            <li><a href="#" class="hover:text-brand-pink transition-colors">Avís legal</a></li>
          </ul>
        </div>

        <p class="text-[1.5dvh] lg:text-[1.7dvh] text-gray-900 text-right">
          Desenvolupat per
          <a href="#" class="text-brand-pink hover:underline font-medium transition-colors">
            GNA Hotel Solutions
          </a>
        </p>

      </div>
    </div>

  </footer>
</template>