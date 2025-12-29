<template>
  <section class="hero-section">
    <div class="hero-carousel">
      <MDBCarousel v-model="carousel1" :items="items1" fade />
    </div>

    <div class="hero-overlay">
      <h1>CV. Berkah Doa Bunda</h1>
      <p>Contractor Specialist Epoxy, Decorative Painting & Waterproofing</p>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { MDBCarousel } from "mdb-vue-ui-kit";

import slide1 from "../assets/slide1.png";
import slide2 from "../assets/slide2.png";
import slide3 from "../assets/slide3.png";

const items1 = [
  { src: slide1, alt: "Slide 1", label: "", caption: "" },
  { src: slide2, alt: "Slide 2", label: "", caption: "" },
  { src: slide3, alt: "Slide 3", label: "", caption: "" },
];

const carousel1 = ref(0);
</script>
<style scoped>
.hero-section {
  position: relative;
  height: 500px;
  overflow: hidden;
}

/* Kunci ukuran carousel */
.hero-carousel,
.hero-carousel :deep(.carousel),
.hero-carousel :deep(.carousel-inner),
.hero-carousel :deep(.carousel-item),
.hero-carousel :deep(img) {
  height: 100%;
}

.hero-carousel img {
  width: 100%;
  object-fit: cover;
}

/* Overlay benar-benar terkunci */
.hero-overlay {
  position: absolute;
  inset: 0;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  text-align: center;
  color: white;
  z-index: 10;

  background: rgba(0, 0, 0, 0.45);
  padding: 2rem;

  backdrop-filter: blur(8px);
}

/* Title */
.hero-overlay h1 {
  font-size: clamp(2.2rem, 5vw, 3.5rem);
  font-weight: 700;
  margin-bottom: 0.75rem;
}

/* Subtitle */
.hero-overlay p {
  font-size: clamp(1rem, 2.5vw, 1.4rem);
  max-width: 720px;
  line-height: 1.6;
}
</style>
