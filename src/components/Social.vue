<template>
  <div class="social">
    <a
      href="https://www.linkedin.com/in/javier-rojas-43324b143/"
      target="_blank"
      ><i class="fa-brands fa-linkedin"></i
    ></a>
    <a href="https://github.com/jpundonor" target="_blank"
      ><i class="fa-brands fa-github"></i
    ></a>
    <a href="https://www.instagram.com/jpundonor/" target="_blank"
      ><i class="fa-brands fa-instagram"></i
    ></a>
  </div>
</template>

<style scoped>
.social {
  @apply before:content-[''] before:w-0.5 before:h-16 before:bg-yellow-300;
  @apply hidden fixed lg:flex flex-col gap-5 items-center top-1/2 pl-2 xl:pl-10 transition-all duration-300 transform -translate-y-1/2 z-50;
  @apply after:content-[''] after:w-0.5 after:h-16 after:bg-yellow-300;
  a {
    @apply text-3xl hover:scale-125;
  }
}
</style>
