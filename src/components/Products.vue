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
    title: "Pengecatan Lapangan Indoor & Outdoor",
    desc: "Lapangan olahraga dengan standar profesional",
    images: [sportFlooringImg],
  },
  {
    title: "Pengecatan Pabrik & Gudang",
    desc: "Lantai industri kuat, rapi, dan tahan lama",
    images: [Epoxy1, Epoxy3],
  },
  {
    title: "Pengecatan Marka Jalan / Road Marking",
    desc: "Garis marka jelas dan tahan aus",
    images: [roadMarkingImg],
  },
  {
    title: "Pengecatan Jembatan",
    desc: "Pelapisan pelindung struktur jembatan",
    images: [protectiveImg],
  },
  {
    title: "Pengecatan Protective Coating",
    desc: "Perlindungan permukaan dari korosi & cuaca",
    images: [protectiveImg],
  },
  {
    title: "Pengecatan Waterproofing",
    desc: "Solusi anti bocor untuk bangunan",
    images: [waterproofingImg],
  },
  {
    title: "Jasa Decorative Flooring",
    desc: "Finishing lantai estetik & modern",
    images: [decorativeImg],
  },
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
  background: linear-gradient(135deg, #5dade2, #1e3c72, #2a5298);
  color: white;
}

/* ===== TITLE ===== */
#produk h2 {
  font-weight: 700;
  letter-spacing: 0.5px;
}

/* ===== SCROLL WRAPPER ===== */
.produk-scroll-wrapper {
  overflow-x: auto;
  padding: 8px 0 16px;
  scrollbar-width: none;
}
.produk-scroll-wrapper::-webkit-scrollbar {
  display: none;
}

.produk-scroll {
  display: flex;
  gap: 20px;
  padding: 4px 2px;
}

/* ===== CARD ===== */
.produk-card {
  min-width: 200px;
  max-width: 200px;
  padding: 14px;
  border-radius: 18px;

  background: rgba(255, 255, 255, 0.16);
  backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.28);

  box-shadow:
    0 10px 25px rgba(0, 0, 0, 0.25),
    inset 0 1px 0 rgba(255, 255, 255, 0.25);

  color: white;
  cursor: pointer;

  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
}

.produk-card:hover {
  transform: translateY(-8px);
  box-shadow:
    0 18px 35px rgba(0, 0, 0, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.35);
}

/* IMAGE */
.produk-card img {
  width: 100%;
  height: 120px;
  object-fit: cover;
  border-radius: 14px;
  margin-bottom: 10px;
}

/* TEXT */
.produk-card h6 {
  font-size: 0.95rem;
  font-weight: 700;
  margin-bottom: 4px;
}

.produk-card p {
  font-size: 0.8rem;
  opacity: 0.9;
  margin: 0;
}

/* ===== MODAL OVERLAY ===== */
.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(8, 15, 30, 0.75);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
  padding: 16px;
}

/* ===== MODAL CONTENT ===== */
.modal-content {
  max-width: 480px;
  width: 100%;
  padding: 24px;

  background: rgba(255, 255, 255, 0.18);
  backdrop-filter: blur(18px);
  border-radius: 24px;

  border: 1px solid rgba(255, 255, 255, 0.35);

  box-shadow:
    0 25px 60px rgba(0, 0, 0, 0.55),
    inset 0 1px 0 rgba(255, 255, 255, 0.4);

  color: white;
  text-align: center;

  animation: modalIn 0.35s ease;
}

/* MODAL IMAGE */
.modal-content img {
  max-height: 240px;
  width: 100%;
  object-fit: cover;
  border-radius: 18px;
}

/* MODAL TEXT */
.modal-content h5 {
  font-weight: 700;
  margin-top: 10px;
}

.modal-content p {
  font-size: 0.9rem;
  opacity: 0.9;
}

/* NAV IMAGE */
.modal-content .btn {
  border-radius: 999px;
  font-weight: 600;
}

/* ===== ANIMATION ===== */
@keyframes modalIn {
  from {
    transform: translateY(20px) scale(0.96);
    opacity: 0;
  }
  to {
    transform: translateY(0) scale(1);
    opacity: 1;
  }
}
</style>
