<template>
  <section id="projects" class="backdrop-brightness-[0.4] max-w-full p-0">
    <div class="p-8 max-w-screen-lg m-auto pb-20 md:py-20">
      <h2>{{ $t("projects.title") }}</h2>

      <div
        v-for="(project, index) in projects"
        :key="index"
        :class="`project-container${index % 2 ? '--reverse' : ''}`"
      >
        <div class="project-card">
          <h3 :class="`project-card__title${index % 2 ? '--reverse' : ''}`">
            <a
              :href="project.urls.page"
              target="_blank"
              rel="noopener noreferrer"
            >
              {{ project.name }}
            </a>
          </h3>
          <div class="relative row-span-6">
            <p
              :class="`project-card__description${
                index % 2 ? '--reverse' : ''
              }`"
            >
              {{ project.description }}
            </p>
          </div>
          <ul :class="`project-card__techstack${index % 2 ? '--reverse' : ''}`">
            <li v-for="(tech, index) in project.technologies" :key="index">
              {{ tech }}
            </li>
          </ul>
          <div :class="`project-card__links${index % 2 ? '--reverse' : ''}`">
            <a
              v-if="project.urls.github"
              :href="project.urls.github"
              target="_blank"
            >
              <i class="fa-brands fa-github"></i>
            </a>
            <a
              v-if="project.urls.page"
              :href="project.urls.page"
              target="_blank"
            >
              <i class="fas fa-external-link-alt"></i>
            </a>
          </div>
        </div>
        <div class="project-card__img-container">
          <a
            :href="project.urls.page"
            target="_blank"
            rel="noopener noreferrer"
          >
            <img
              :src="`../../src/assets/${project.image}`"
              :alt="project.imageAlt"
              class="project-card__img"
            />
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { projectsData } from "../data/projectsData";
export default {
  name: "Projects",
  data() {
    return {
      toggle: false,
    };
  },
  computed: {
    projects() {
      return projectsData[this.$i18n.locale];
    },
  },
};
</script>

<style scoped>
.project-container {
  @apply flex justify-center relative md:py-14 py-10;
}
.project-container--reverse {
  @apply flex flex-row-reverse justify-center relative md:py-14 py-10;
}

.project-card {
  @apply grid grid-rows-8 bg-slate-800 bg-opacity-75 backdrop-blur z-10;
  @apply md:grid-rows-9 md:w-80 h-96 md:h-72 md:bg-transparent md:backdrop-blur-0;
}

.project-card__title {
  @apply text-2xl py-2 row-span-2 self-center text-center text-orange-500 md:text-start;
}
.project-card__title--reverse {
  @apply text-2xl py-2 row-span-2 self-center text-center text-orange-500  md:text-end;
}

.project-card__description {
  @apply px-8 py-4 text-justify text-yellow-300;
  @apply md:bg-yellow-300 md:text-fuchsia-950 md:w-96 md:absolute;
}
.project-card__description--reverse {
  @apply px-8 py-4 text-justify text-yellow-300;
  @apply md:bg-yellow-300 md:text-fuchsia-950 md:w-96 md:absolute right-0;
}

.project-card__techstack {
  @apply flex flex-wrap gap-3 justify-center md:justify-start md:self-end;
}
.project-card__techstack--reverse {
  @apply flex flex-wrap gap-3 justify-center self-end md:justify-end;
}

.project-card__links {
  @apply flex gap-x-5 pr-5 md:py-0 text-xl justify-end pb-5 md:pb-0 md:justify-start z-20;
  & a {
    @apply hover:scale-125;
  }
}
.project-card__links--reverse {
  @apply flex gap-x-5 pr-5 md:py-0 text-xl pb-5 md:pb-0 justify-end z-20;
  & a {
    @apply hover:scale-125;
  }
}

.project-card__img-container {
  @apply absolute bg-red-950 h-96 cursor-pointer md:h-72 md:static -z-10 md:z-0;
}
.project-card__img {
  @apply w-full h-full object-cover aspect-video transition-all duration-500 ease-in-out;
  @apply mix-blend-lighten sepia-[0.2] grayscale-[0.7] contrast-125;
  @apply hover:mix-blend-normal hover:sepia-0 hover:grayscale-0 hover:contrast-100;
}
</style>
