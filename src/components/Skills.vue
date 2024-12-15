<template>
  <div class="md:w-5/6">
    <h3 class="text-xl text-center pb-5">{{ $t("skills.title") }}</h3>
    <div class="grid grid-cols-4 md:grid-cols-5 gap-4">
      <div v-for="skill in skills" :key="skill" class="justify-items-center">
        <i
          :class="`text-3xl md:text-4xl ${skill.icon} ${skill.color}  transition-all duration-500`"
        ></i>
        <p>{{ skill.name }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Skills",
  data() {
    return {
      skills: [
        {
          name: "JavaScript",
          icon: "fa-brands fa-js",
          color: "hover:text-yellow-400",
        },
        {
          name: "Vue.js",
          icon: "fa-brands fa-vuejs",
          color: "hover:text-emerald-500",
        },
        {
          name: "React.js",
          icon: "fa-brands fa-react",
          color: "hover:text-cyan-500",
        },
        {
          name: "HTML5",
          icon: "fa-brands fa-html5",
          color: "hover:text-orange-700",
        },
        { name: "CSS3", icon: "fa-brands fa-css", color: "hover:text-sky-500" },
        {
          name: "Sass",
          icon: "fa-brands fa-sass",
          color: "hover:text-pink-500",
        },
        {
          name: "Bootstrap",
          icon: "fa-brands fa-bootstrap",
          color: "hover:text-purple-700",
        },
        {
          name: "GitHub",
          icon: "fa-brands fa-github",
          color: "hover:text-black",
        },
      ],
    };
  },
};
</script>
