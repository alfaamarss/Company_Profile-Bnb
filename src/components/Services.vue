<template>
  <section id="layanan" class="py-5">
    <div class="container">
      <h2 class="mb-5 text-center text-white">Layanan Kami</h2>

      <div class="layanan-wrapper" ref="wrapper">
        <div class="layanan-track" :style="mobileStyle">
          <div class="layanan-slide fade-up" v-for="(layanan, index) in layananList" :key="index" ref="slidesRefs">
            <div class="card shadow-sm h-100 text-center" @click="openModal(layanan)">
              <img :src="layanan.img" class="card-img-top mx-auto mt-3" style="width: 80px; height: 80px" />
              <div class="card-body">
                <h5 class="card-title fw-bold">{{ layanan.title }}</h5>
                <p class="card-text">{{ layanan.desc }}</p>
              </div>
            </div>
          </div>
        </div>

        <!-- BUTTON SLIDER -->
        <div v-if="isMobile" class="slider-nav">
          <button class="left" @click="prev">‹</button>
          <button class="right" @click="next">›</button>
        </div>
      </div>
    </div>

    <!-- MODAL (taruh di section supaya tidak terpotong) -->
    <div v-if="selectedLayanan" class="modal-overlay" @click.self="closeModal">
      <div class="modal-content glass-modal">
        <img :src="selectedLayanan.img" class="img-fluid mb-3" />
        <h5 class="fw-bold mb-2">{{ selectedLayanan.title }}</h5>
        <p>{{ selectedLayanan.desc }}</p>
        <button class="btn btn-primary mt-3" @click="closeModal">Tutup</button>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, computed, nextTick } from "vue";

import epoxyImg from "../assets/epoxy.png";
import waterproofingImg from "../assets/waterproofing.png";
import roadMarkingImg from "../assets/road-marking.png";
import protectiveImg from "../assets/protective.png";
import sportFlooringImg from "../assets/sport-flooring.png";
import decorativeImg from "../assets/decorative.png";
import floorHardenerImg from "../assets/floor-hardener.png";
import membranImg from "../assets/membran.png";

type Layanan = { title: string; desc: string; img: string };

const layananList: Layanan[] = [
  { title: "Jasa Pengecatan Lantai Epoxy", desc: "Lantai kuat dan tahan lama", img: epoxyImg },
  { title: "Jasa Waterproofing", desc: "Lindungi bangunan dari air", img: waterproofingImg },
  { title: "Jasa Road Line Marking", desc: "Tanda batas lantai dan area", img: roadMarkingImg },
  { title: "Jasa Protective Coating", desc: "Perlindungan permukaan logam/non-logam", img: protectiveImg },
  { title: "Jasa Sport Flooring", desc: "Lapangan olahraga berkualitas", img: sportFlooringImg },
  { title: "Jasa Decorative Flooring", desc: "Hiasan lantai dekoratif", img: decorativeImg },
  { title: "Jasa Floor Hardener", desc: "Finishing beton kuat", img: floorHardenerImg },
  { title: "Jasa Membran Bakar Waterproofing", desc: "Lapisan anti bocor", img: membranImg },
];

const selectedLayanan = ref<Layanan | null>(null);
const isMobile = ref(false);
const current = ref(0);
const wrapper = ref<HTMLElement | null>(null);
const slideWidth = ref(0);

// ref array untuk animasi scroll
const slidesRefs = ref<HTMLElement[]>([]);

const updateSize = () => {
  isMobile.value = window.innerWidth <= 768;
  if (wrapper.value) slideWidth.value = wrapper.value.clientWidth;
};

const next = () => (current.value = (current.value + 1) % layananList.length);
const prev = () => (current.value = (current.value - 1 + layananList.length) % layananList.length);

const mobileStyle = computed(() => (isMobile.value ? { transform: `translateX(-${current.value * slideWidth.value}px)` } : {}));

onMounted(async () => {
  updateSize();
  window.addEventListener("resize", updateSize);

  await nextTick();

  // Intersection Observer untuk animasi scroll
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("visible");
        } else {
          entry.target.classList.remove("visible");
        }
      });
    },
    { threshold: 0.2 }
  );

  slidesRefs.value.forEach((el) => observer.observe(el));
});

const openModal = (item: Layanan) => (selectedLayanan.value = item);
const closeModal = () => (selectedLayanan.value = null);
</script>

<style scoped>
/* Section Layanan */
#layanan {
  overflow-x: hidden;
  padding: 2rem 0;
  background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
  color: white;
}

/* ===== CARD GLASS ===== */
.card {
  border: 1px solid rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  cursor: pointer;
  transition: transform 0.3s, box-shadow 0.3s, border 0.3s;
  color: white;
}

.card:hover {
  transform: translateY(-6px) scale(1.03);
  box-shadow: 0 12px 25px rgba(0, 0, 0, 0.4);
  border-color: rgba(255, 255, 255, 0.35);
}

.card img {
  border-radius: 12px;
  object-fit: cover;
}

/* Layanan track & slides */
.layanan-track {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  transition: transform 0.45s ease;
}

.layanan-slide {
  width: 100%;
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.6s ease;
}

.layanan-slide.visible {
  opacity: 1;
  transform: translateY(0);
}

/* MOBILE */
@media (max-width: 768px) {
  .layanan-track {
    display: flex;
    gap: 0;
  }

  .layanan-slide {
    min-width: 100%;
    flex: 0 0 100%;
  }

  .slider-nav button {
    background: rgba(255, 255, 255, 0.15);
    color: white;
    border-radius: 12px;
  }
}

/* ===== MODAL ===== */
.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.6);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
}

.modal-content {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  padding: 2rem;
  max-width: 400px;
  width: 90%;
  text-align: center;
  color: white;
  box-shadow: 0 12px 25px rgba(0, 0, 0, 0.4);
  transition: all 0.3s ease;
}
</style>
