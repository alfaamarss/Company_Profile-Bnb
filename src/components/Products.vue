<template>
  <section id="produk" class="py-5">
    <div class="container">
      <h2 class="mb-4 text-center text-white">Produk Kami</h2>

      <div class="produk-scroll-wrapper">
        <div class="produk-scroll d-flex gap-3">
          <div v-for="(produk, index) in produkList" :key="index" class="produk-card card text-center" @click="openProduk(produk)">
            <img :src="produk.images[0]" class="img-fluid mb-2" />
            <h6 class="fw-bold">{{ produk.title }}</h6>
            <p class="mb-0">{{ produk.desc }}</p>
          </div>
        </div>
      </div>
    </div>

    <!-- MODAL GLASS -->
    <div v-if="selectedProduk" class="modal-overlay" @click.self="closeProduk">
      <div class="modal-content glass-modal">
        <img :src="selectedProduk.images[currentImage]" class="img-fluid mb-3 rounded" />

        <!-- NAV IMAGE -->
        <div v-if="selectedProduk.images.length > 1" class="d-flex justify-content-between mb-3">
          <button class="btn btn-light btn-sm" @click="prevImage">‹</button>
          <button class="btn btn-light btn-sm" @click="nextImage">›</button>
        </div>

        <h5 class="fw-bold mb-2">{{ selectedProduk.title }}</h5>
        <p>{{ selectedProduk.desc }}</p>

        <button class="btn btn-primary mt-3" @click="closeProduk">Tutup</button>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from "vue";

/* ===== TYPE ===== */
interface Produk {
  title: string;
  desc: string;
  images: string[];
}

/* ===== IMAGES ===== */
import Epoxy1 from "../assets/product/Epoxy1.jpeg";
import Epoxy3 from "../assets/product/Epoxy3.jpeg";

import waterproofingImg from "../assets/waterproofing.png";
import roadMarkingImg from "../assets/road-marking.png";
import protectiveImg from "../assets/protective.png";
import sportFlooringImg from "../assets/sport-flooring.png";
import decorativeImg from "../assets/decorative.png";
import floorHardenerImg from "../assets/floor-hardener.png";
import membranImg from "../assets/membran.png";

/* ===== DATA ===== */
const produkList: Produk[] = [
  {
    title: "Jasa Pengecatan Lantai Epoxy",
    desc: "Lantai kuat dan tahan lama",
    images: [Epoxy1, Epoxy3],
  },
  { title: "Jasa Waterproofing", desc: "Lindungi bangunan dari air", images: [waterproofingImg] },
  { title: "Jasa Road Line Marking", desc: "Tanda batas lantai dan area", images: [roadMarkingImg] },
  { title: "Jasa Protective Coating", desc: "Perlindungan permukaan", images: [protectiveImg] },
  { title: "Jasa Sport Flooring", desc: "Lapangan olahraga", images: [sportFlooringImg] },
  { title: "Jasa Decorative Flooring", desc: "Hiasan lantai", images: [decorativeImg] },
  { title: "Jasa Floor Hardener", desc: "Finishing beton", images: [floorHardenerImg] },
  { title: "Jasa Membran Bakar", desc: "Anti bocor", images: [membranImg] },
];

/* ===== MODAL ===== */
const selectedProduk = ref<Produk | null>(null);
const currentImage = ref(0);

const openProduk = (produk: Produk) => {
  selectedProduk.value = produk;
  currentImage.value = 0;
};

const closeProduk = () => {
  selectedProduk.value = null;
};

const nextImage = () => {
  if (!selectedProduk.value) return;
  currentImage.value = (currentImage.value + 1) % selectedProduk.value.images.length;
};

const prevImage = () => {
  if (!selectedProduk.value) return;
  currentImage.value = (currentImage.value - 1 + selectedProduk.value.images.length) % selectedProduk.value.images.length;
};
</script>

<style scoped>
#produk {
  background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
  color: white;
}

/* SCROLL */
.produk-scroll-wrapper {
  display: flex;
  overflow-x: auto;
  gap: 1rem;
  padding-bottom: 1rem;
  scrollbar-width: none;
}
.produk-scroll-wrapper::-webkit-scrollbar {
  display: none;
}

/* CARD */
.produk-card {
  min-width: 180px;
  padding: 1rem;
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.25);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  color: white;
  cursor: pointer;
  transition: 0.3s ease;
}

.produk-card:hover {
  transform: translateY(-6px) scale(1.03);
  box-shadow: 0 12px 28px rgba(0, 0, 0, 0.4);
}

.produk-card img {
  height: 100px;
  width: 100%;
  object-fit: cover;
  border-radius: 12px;
}

.produk-card p {
  font-size: 0.85rem;
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
  max-width: 420px;
  width: 90%;
  text-align: center;
  color: white;
  box-shadow: 0 12px 25px rgba(0, 0, 0, 0.4);
  animation: modalIn 0.35s ease;
}

@keyframes modalIn {
  from {
    transform: scale(0.8);
    opacity: 0;
  }
  to {
    transform: scale(1);
    opacity: 1;
  }
}

.produk-card img {
  width: 100%;
  height: 110px; /* FIX HEIGHT */
  object-fit: cover; /* POTONG RAPI */
  border-radius: 12px;
}
</style>
