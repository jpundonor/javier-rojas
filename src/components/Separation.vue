<template>
  <div class="relative">
    <canvas
      ref="canvas"
      class="w-full absolute inset-0 z-20 pointer-events-none"
    ></canvas>

    <div v-if="isFrist" class="bg-fuchsia-950 brightness-[0.4]">
      <div
        class="bg-fuchsia-950 brightness-[2.5] h-32 relative"
        style="clip-path: polygon(0 0, 0 0, 100% 0, 70% 100%)"
      ></div>
    </div>
    <div
      v-if="!isFrist"
      class="bg-fuchsia-950 brightness-[0.4] h-32 relative"
      style="clip-path: polygon(0 0, 0 0, 100% 0, 70% 100%)"
    ></div>
  </div>
</template>

<script>
export default {
  name: "CircleCanvas",
  props: {
    isFrist: Boolean,
  },
  mounted() {
    this.drawCircles();
  },
  methods: {
    drawCircles() {
      const canvas = this.$refs.canvas;
      const ctx = canvas.getContext("2d");

      // Se ajusta tamaño del canvas
      canvas.width = canvas.offsetWidth;
      canvas.height = canvas.offsetHeight;

      // Crear círculos aleatorios
      const circles = Array.from({ length: 10 }, () => {
        let x, y;

        do {
          x = Math.random() * canvas.width; // Coordenada X
          y = (Math.random() * canvas.height) / 2; // Limitar a la mitad superior
        } while (this.isNearClipPath(x, y, canvas.width, canvas.height)); // Verificar si está cerca del clip-path

        return {
          x,
          y,
          r: Math.random() * 10 + 5, // Radio entre 5 y 15 px
          opacity: Math.random() * 0.5 + 0.5, // Opacidad entre 0.5 y 1
        };
      });

      // Dibujar los círculos en el canvas
      circles.forEach((circle) => {
        ctx.beginPath();
        ctx.arc(circle.x, circle.y, circle.r, 0, Math.PI * 2);
        ctx.fillStyle = `rgba(255, 255, 255, ${circle.opacity})`;
        ctx.fill();
      });
    },

    // Verifica si un punto está cerca del área del clip-path
    isNearClipPath(x, y, width, height) {
      const threshold = 20; // Margen seguro para evitar los bordes

      // Representación simplificada del clip-path: polygon(0 0, 0 0, 100% 0, 70% 100%);
      const clipPathSlope = height / (width * 0.3); // Pendiente de la línea del clip-path
      const yClipPath = clipPathSlope * (width - x); // Coordenada Y según el clip-path

      // Evitar bordes o el área del clip-path
      return (
        x < threshold || // Izquierda
        x > width - threshold || // Derecha
        y < threshold || // Superior
        y > yClipPath - threshold // Cercano al clip-path
      );
    },
  },
};
</script>
