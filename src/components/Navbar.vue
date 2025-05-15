<template>
  <nav :class="showNavbar ? 'translate-y-0' : '-translate-y-full'">
    <div class="basis-1/2">
      <a class="text-xl font-bold" href="#">Javier Rojas</a>
    </div>
    <div class="hidden gap-5 md:flex basis-1/3 justify-end text-nowrap">
      <a href="#about">{{ $t("navbar.about") }}</a>
      <a href="#projects">{{ $t("navbar.projects") }}</a>
      <a href="#contact">{{ $t("navbar.contact") }}</a>
    </div>
    <div class="hidden md:flex basis-1/6 justify-end">
      <a href="/assets/CV_Javier_Rojas.pdf" target="_blank">CV</a>
    </div>
    <div
      class="cursor-pointer basis-1/2 text-end md:hidden"
      @click="toggleMenu"
    >
      <i class="fa-solid fa-bars"></i>
    </div>
    <div
      :class="
        'navbar__colapsed ' + (isMenuOpen ? ' max-h-96 p-5' : ' max-h-0 p-0 ')
      "
    >
      <a href="#about">{{ $t("navbar.about") }}</a>
      <a href="#projects">{{ $t("navbar.projects") }}</a>
      <a href="#contact">{{ $t("navbar.contact") }}</a>
      <a href="/assets/CV_Javier_Rojas.pdf" target="_blank">CV</a>
    </div>
  </nav>
</template>

<script>
import { onMounted, onUnmounted, ref } from "vue";
export default {
  name: "Navbar",
  data() {
    return {
      isMenuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
  },

  setup() {
    const showNavbar = ref(true);
    let lastScrollY = window.scrollY;

    const handleScroll = () => {
      const currentScrollY = window.scrollY;
      showNavbar.value = currentScrollY < lastScrollY || currentScrollY <= 0;
      lastScrollY = currentScrollY;
    };

    onMounted(() => {
      window.addEventListener("scroll", handleScroll);
    });

    onUnmounted(() => {
      window.removeEventListener("scroll", handleScroll);
    });

    return { showNavbar };
  },
};
</script>

<style scoped>
.navbar__colapsed {
  @apply flex flex-col gap-5 absolute bottom-0 left-0 w-full px-5 bg-black bg-opacity-75;
  @apply transition-all duration-500 ease-in-out z-20 md:hidden translate-y-full overflow-hidden;
}
</style>
