<template>
  <Navbar />
  <SwitchLang />
  <Social />
  <About />
  <Separation :is-frist="true" />
  <Projects />
  <Separation :is-frist="false" />
  <Contact />
  <Footer />
</template>

<script setup>
import Navbar from "./components/Navbar.vue";
import About from "./components/About.vue";
import SwitchLang from "./components/SwitchLang.vue";
import Projects from "./components/Projects.vue";
import Contact from "./components/Contact.vue";
import Footer from "./components/Footer.vue";
import Separation from "./components/Separation.vue";
import Social from "./components/Social.vue";
</script>

<style scoped></style>
