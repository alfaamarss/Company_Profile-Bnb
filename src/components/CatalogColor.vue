<template>
  <section id="warna" class="py-5">
    <div class="container">
      <h2 class="mb-5 text-center text-white">Katalog Warna</h2>

      <div class="warna-wrapper" ref="wrapper">
        <div class="warna-track">
          <div class="warna-slide" v-for="(color, index) in loopColors" :key="index">
            <div class="color-card text-center p-3 rounded shadow" @click="openModal(color)">
              <div class="color-box mb-2 mx-auto rounded" :style="{ backgroundColor: color.hex }"></div>
              <span>{{ color.name }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal -->
    <div v-if="selectedColor" class="modal-overlay" @click.self="closeModal">
      <div class="modal-content">
        <h5 class="fw-bold mb-2">{{ selectedColor.name }}</h5>
        <div class="modal-color-box" :style="{ backgroundColor: selectedColor.hex }"></div>
        <p>Hex: {{ selectedColor.hex }}</p>
        <button class="btn btn-primary mt-3" @click="closeModal">Tutup</button>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from "vue";

interface Color {
  name: string;
  hex: string;
}

const colors: Color[] = [
  { name: "Alabaster", hex: "#FAFAFA" },
  { name: "Grey", hex: "#808080" },
  { name: "Mint Green", hex: "#98FF98" },
  { name: "Dark Green", hex: "#006400" },
  { name: "Traffic Blue", hex: "#007ACC" },
  { name: "Sky Blue", hex: "#87CEEB" },
  { name: "Ivory", hex: "#FFFFF0" },
  { name: "Light Grey", hex: "#D3D3D3" },
  { name: "Pastel Green", hex: "#77DD77" },
  { name: "Yellow Green", hex: "#9ACD32" },
  { name: "Traffic Yellow", hex: "#FFD700" },
  { name: "Victoria", hex: "#8B5F65" },
  { name: "White", hex: "#FFFFFF" },
  { name: "Medium Grey", hex: "#A9A9A9" },
  { name: "Light Blue", hex: "#ADD8E6" },
  { name: "Leaf Green", hex: "#228B22" },
  { name: "Traffic Red", hex: "#FF0000" },
  { name: "Blue Purple", hex: "#8A2BE2" },
];

// Duplikasi untuk looping seamless
const loopColors = [...colors, ...colors];

const isMobile = ref(false);
const wrapper = ref<HTMLDivElement | null>(null);
let intervalId: any = null;

// Modal
const selectedColor = ref<Color | null>(null);
const openModal = (color: Color) => (selectedColor.value = color);
const closeModal = () => (selectedColor.value = null);

// Resize & cek mobile
const updateSize = () => {
  isMobile.value = window.innerWidth <= 768;
};

// Scroll ke kanan untuk auto-slide
const autoSlide = () => {
  if (!isMobile.value || !wrapper.value) return;
  const container = wrapper.value;
  const scrollStep = container.clientWidth / 2;
  if (container.scrollLeft + scrollStep >= container.scrollWidth / 2) {
    container.scrollLeft = 0; // reset untuk looping
  } else {
    container.scrollLeft += scrollStep;
  }
};

// Tombol manual
const next = () => {
  if (!isMobile.value || !wrapper.value) return;
  wrapper.value.scrollLeft += wrapper.value.clientWidth / 2;
};

const prev = () => {
  if (!isMobile.value || !wrapper.value) return;
  wrapper.value.scrollLeft -= wrapper.value.clientWidth / 2;
};

onMounted(() => {
  updateSize();
  window.addEventListener("resize", updateSize);

  intervalId = setInterval(autoSlide, 3000);
});

onBeforeUnmount(() => {
  window.removeEventListener("resize", updateSize);
  clearInterval(intervalId);
});
</script>

<style scoped>
/* Section background biru gradient */
#warna {
  padding: 2rem 0;
  background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
  color: white;
}

/* Wrapper & Track */
.warna-wrapper {
  position: relative;
  overflow-x: auto;
  scroll-behavior: smooth;
  scroll-snap-type: x mandatory;
}

.warna-track {
  display: flex;
  gap: 1rem;
  padding: 1rem;
}

.warna-slide {
  min-width: 120px;
  flex-shrink: 0;
  scroll-snap-align: start;
}

/* Glass Card Effect */
.color-card {
  background: rgba(255, 255, 255, 0.15); /* semi-transparent */
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px); /* Safari */
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  border-radius: 16px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  cursor: pointer;
  transition: transform 0.3s, box-shadow 0.3s, border 0.3s;
  padding: 1rem;
  text-align: center;
  color: white;
}

.color-card:hover {
  transform: translateY(-5px) scale(1.05);
  box-shadow: 0 12px 25px rgba(0, 0, 0, 0.4);
  border-color: rgba(255, 255, 255, 0.5);
}

/* Color Box */
.color-box {
  width: 80px;
  height: 80px;
  border: 3px solid rgba(255, 255, 255, 0.6);
  border-radius: 12px;
  margin: 0 auto 0.5rem auto;
}
/* Modal Glass Effect */
.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-content {
  background: rgba(255, 255, 255, 0.15); /* semi-transparent */
  backdrop-filter: blur(10px); /* efek blur glass */
  -webkit-backdrop-filter: blur(10px); /* untuk Safari */
  padding: 2rem;
  border-radius: 16px;
  max-width: 400px;
  width: 90%;
  text-align: center;
  color: white; /* teks putih biar terlihat di atas glass */
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.4); /* shadow untuk pop */
  border: 1px solid rgba(255, 255, 255, 0.3); /* garis tipis di pinggir */
}

.modal-color-box {
  width: 120px;
  height: 120px;
  margin: 1rem auto;
  border: 3px solid #fff; /* biar terlihat di glass */
  border-radius: 12px;
}

/* Desktop grid */
@media (min-width: 769px) {
  .warna-wrapper {
    overflow-x: visible;
  }
  .warna-track {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
  }
  .warna-slide {
    min-width: auto;
  }
}
</style>
