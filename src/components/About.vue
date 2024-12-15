<template>
  <section id="about" class="py-20">
    <div class="about__container">
      <div class="about__info">
        <h2>{{ $t("about.title") }}</h2>
        <p class="about__description">{{ $t("about.description") }}</p>
        <Skills />
      </div>
      <div class="about__img-container">
        <img
          src="../assets/perfil.webp"
          alt="{{ $t('about.imageAlt') }}"
          class="about__img"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import Skills from "./Skills.vue";
</script>

<style scoped>
.about__container {
  @apply grid grid-cols-1 items-center md:grid-cols-3 md:mt-10;
}
.about__info {
  @apply col-span-2 justify-self-center;
}
.about__description {
  @apply md:w-5/6 text-justify pb-5;
}
.about__img-container {
  @apply h-80 overflow-hidden mt-5 md:mt-0 justify-self-center border-b-2 border-r-2 rounded-3xl;
}
.about__img {
  @apply rounded-3xl drop-shadow-2xl h-full object-contain transition-all duration-500 mix-blend-lighten sepia-[0.2] grayscale-[0.8] contrast-125;
  @apply hover:-translate-x-2 hover:-translate-y-2 hover:mix-blend-normal hover:sepia-0 hover:grayscale-0 hover:contrast-100;
}
</style>
