<template>
  <div class="switch-lang">
    <label class="cursor-pointer">
      <input
        type="radio"
        @change="switchLang(activeLang)"
        v-model="activeLang"
        value="es"
        class="peer hidden"
      />
      <span class="switch-lang__frist-button"> ES </span>
    </label>
    <label class="cursor-pointer">
      <input
        type="radio"
        @change="switchLang(activeLang)"
        v-model="activeLang"
        value="en"
        class="peer hidden"
      />
      <span class="switch-lang__second-button"> EN </span>
    </label>
  </div>
</template>

<script>
export default {
  name: "SwitchLang",
  data() {
    return {
      activeLang: "es",
    };
  },
  methods: {
    switchLang(lang) {
      this.$i18n.locale = lang;
      localStorage.setItem("lang", lang);
    },
  },
  created() {
    const savedLang = localStorage.getItem("lang") || "es";
    this.$i18n.locale = savedLang;
    this.activeLang = savedLang;
  },
};
</script>

<style scoped>
.switch-lang {
  @apply flex gap-1 p-1 rounded-full bg-gray-700 border border-orange-300 w-max shadow-md absolute right-0 mr-10 my-5 mt-20;
}
.switch-lang__frist-button {
  @apply p-1 text-sm rounded-full peer-checked:bg-orange-500 transition-all duration-700 ease-in-out;
  @apply hover:bg-orange-400 hover:bg-opacity-50;
}
.switch-lang__second-button {
  @apply p-1 text-sm rounded-full peer-checked:bg-orange-500 transition-all duration-700 ease-in-out;
  @apply hover:bg-orange-400 hover:bg-opacity-50;
}
</style>
