<template>
  <section id="warna" class="py-5">
    <div class="container">
      <h2 class="mb-5 text-center text-white">Katalog Warna</h2>

      <!-- Color Reference Generator -->
      <div class="custom-color-generator mb-5 text-center">
        <h5 class="mb-3">Buat Referensi Warna</h5>
        <input type="color" v-model="customHex" class="color-picker mb-3" />

        <!-- Card Preview -->
        <div class="color-card text-center mx-auto p-3 rounded shadow custom-card" @click="openModal({ hex: customHex, name: 'Custom Color' })">
          <div class="color-box mb-2 mx-auto rounded" :style="{ backgroundColor: customHex }"></div>
          <span>{{ customHex }}</span>
        </div>
      </div>

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
import { ref, onMounted, onBeforeUnmount, computed } from "vue";

interface Color {
  name: string;
  hex: string;
}

// Default Colors
const colors: Color[] = [
  { name: "Alabaster", hex: "#FAFAFA" },
  { name: "Grey", hex: "#808080" },
  { name: "Mint Green", hex: "#98FF98" },
  { name: "Dark Green", hex: "#006400" },
  { name: "Traffic Blue", hex: "#007ACC" },
  { name: "Sky Blue", hex: "#87CEEB" },
  { name: "Light Grey", hex: "#D3D3D3" },
  { name: "Pastel Green", hex: "#77DD77" },
  { name: "Yellow Green", hex: "#9ACD32" },
  { name: "Traffic Yellow", hex: "#FFD700" },
  { name: "Victoria", hex: "#8B5F65" },
  { name: "White", hex: "#FFFFFF" },
  { name: "Medium Grey", hex: "#A9A9A9" },
  { name: "Leaf Green", hex: "#228B22" },
  { name: "Traffic Red", hex: "#FF0000" },
  { name: "Blue Purple", hex: "#8A2BE2" },
];

const isMobile = ref(false);
const wrapper = ref<HTMLDivElement | null>(null);
let intervalId: any = null;

// Loop Colors untuk mobile
const loopColors = computed(() => {
  return isMobile.value ? [...colors, ...colors] : colors;
});

// Modal
const selectedColor = ref<Color | null>(null);
const openModal = (color: Color) => (selectedColor.value = color);
const closeModal = () => (selectedColor.value = null);

// Resize check
const updateSize = () => {
  isMobile.value = window.innerWidth <= 768;
};

// Auto slide (mobile only)
const autoSlide = () => {
  if (!isMobile.value || !wrapper.value) return;

  const container = wrapper.value;
  const scrollStep = container.clientWidth / 1.5;

  if (container.scrollLeft + scrollStep >= container.scrollWidth / 2) {
    container.scrollLeft = 0;
  } else {
    container.scrollLeft += scrollStep;
  }
};

// Custom color for reference only
const customHex = ref("#ff0000");

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
#warna {
  padding: 2rem 0;
  background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
  color: white;
}

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

.color-card {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
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

.color-box {
  width: 80px;
  height: 80px;
  border: 3px solid rgba(255, 255, 255, 0.6);
  border-radius: 12px;
  margin: 0 auto 0.5rem auto;
}

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
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  padding: 2rem;
  border-radius: 16px;
  max-width: 400px;
  width: 90%;
  text-align: center;
  color: white;
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.4);
  border: 1px solid rgba(255, 255, 255, 0.3);
}

.modal-color-box {
  width: 120px;
  height: 120px;
  margin: 1rem auto;
  border: 3px solid #fff;
  border-radius: 12px;
}

/* Color generator */
.custom-color-generator .color-picker {
  width: 80px;
  height: 50px;
  border: none;
  cursor: pointer;
}

.custom-color-generator .preview {
  width: 100px;
  height: 50px;
  margin: 0 auto 0.5rem auto;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  border: 2px solid rgba(255, 255, 255, 0.5);
}

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
@media (min-width: 769px) {
  .warna-wrapper {
    scroll-snap-type: none;
  }
}

.custom-color-generator .custom-card {
  width: 140px;
  cursor: pointer;
  transition: transform 0.3s, box-shadow 0.3s, border 0.3s;
}

.custom-color-generator .custom-card:hover {
  transform: translateY(-5px) scale(1.05);
  box-shadow: 0 12px 25px rgba(0, 0, 0, 0.4);
  border-color: rgba(255, 255, 255, 0.5);
}

.custom-color-generator .color-box {
  width: 100px;
  height: 100px;
  border: 3px solid rgba(255, 255, 255, 0.6);
  border-radius: 12px;
  margin: 0 auto 0.5rem auto;
}

.custom-color-generator .color-picker {
  width: 80px;
  height: 50px;
  border: none;
  cursor: pointer;
}
</style>
