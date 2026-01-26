<template>
  <section id="produk" class="py-5">
    <div class="container">
      <h2 class="mb-4 text-center text-white">Produk Kami</h2>

      <div class="produk-scroll-wrapper">
        <div class="produk-scroll d-flex gap-3">
          <div v-for="(produk, index) in produkList" :key="index" class="produk-card card text-center" @click="openProduk(produk)">
            <img :src="produk.images[0]" class="img-fluid mb-2" />
            <h6 class="fw-bold">{{ produk.title }}</h6>
            <p class="mb-0">{{ produk.shortDesc }}</p>
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
        <p>{{ selectedProduk.fullDesc }}</p>

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
  shortDesc: string;
  fullDesc: string;
  images: string[];
}

/* ===== IMAGES ===== */

import produk1 from "../assets/product/produk1.png";
import produk2 from "../assets/product/produk2.png";
import produk3 from "../assets/product/produk3.png";
import produk4 from "../assets/product/produk4.png";
import produk5 from "../assets/product/produk5.png";
import produk6 from "../assets/product/produk6.png";
import produk7 from "../assets/product/produk7.png";
import produk8 from "../assets/product/produk8.png";

/* ===== DATA ===== */
const produkList: Produk[] = [
  {
    title: "BDB – Bodycoat Epoxy",
    shortDesc: "Pelapis dasar epoxy untuk menutup pori beton",
    fullDesc:
      "BDBFLOOR BODYCOAT EPOXY merupakan cat epoxy dua komponen yang diformulasikan khusus sebagai pelapis beton sebagai dasar sebelum aplikasi epoxy lanjutan. Berfungsi menutupi pori-pori permukaan beton atau keramik setelah tahap primer.",
    images: [produk1],
  },
  {
    title: "BDB – Mortar Epoxy",
    shortDesc: "Perbaikan beton & retakan, waterproof",
    fullDesc: "BDBFLOOR BMORTAR EPOXY diformulasikan khusus untuk perbaikan dan penyambungan keretakan pada beton, lapisan acian beton rapuh, serta beton lembab. Bersifat waterproof untuk menahan kadar air di dalam beton.",
    images: [produk2],
  },
  {
    title: "BDB – Primer Epoxy Lantai",
    shortDesc: "Lapisan dasar penetrasi epoxy",
    fullDesc: "BDBFLOOR PRIMER EPOXY merupakan cat epoxy dua komponen sebagai pelapis dasar yang berfungsi melakukan penetrasi ke dalam substrat dan meningkatkan daya lekat lapisan epoxy selanjutnya.",
    images: [produk3],
  },
  {
    title: "BDB – Topcoat SL Finish",
    shortDesc: "Epoxy self leveling tebal & anti-selip",
    fullDesc: "BDBFLOOR TOPCOAT SELFLEVELING merupakan epoxy dua komponen sebagai finishing akhir untuk ketebalan > 1.000 micron. Menghasilkan tampilan glossy/semi glossy serta memiliki keunggulan anti-selip dan daya tahan tinggi.",
    images: [produk4],
  },
  {
    title: "BDB – Topcoat Finish Coating",
    shortDesc: "Finishing epoxy tipis & rapi",
    fullDesc: "BDBFLOOR TOPCOAT COATING EPOXY adalah lapisan finish akhir epoxy untuk ketebalan < 1.000 micron dengan hasil glossy atau semi glossy sesuai kebutuhan proyek.",
    images: [produk5],
  },
  {
    title: "BDB – Topcoat PU Finish",
    shortDesc: "Finishing PU tahan cuaca",
    fullDesc: "BDBFLOOR TOPCOAT PU merupakan cat polyurethane dua komponen sebagai lapisan akhir dengan ketahanan cuaca yang sangat baik serta hasil finishing glossy atau semi glossy.",
    images: [produk6],
  },
  {
    title: "Multizinc – Zincromate Primer",
    shortDesc: "Cat dasar anti karat untuk logam",
    fullDesc: "ZINCROMATE PRIMER adalah cat dasar untuk besi dan logam yang berfungsi mencegah karat. Digunakan sebagai pelapis awal pada besi, seng, dan material metal lainnya.",
    images: [produk7],
  },
  {
    title: "Synthetic – Cat Minyak",
    shortDesc: "Cat kayu & besi tahan lama",
    fullDesc: "SYNTHETIC merupakan cat minyak berkualitas tinggi untuk permukaan kayu dan metal. Cocok untuk interior dan eksterior dengan hasil halus, tahan lama, mudah dibersihkan, serta anti jamur.",
    images: [produk8],
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
  font-size: 0.95rem;
  line-height: 1.65;
  letter-spacing: 0.2px;
  color: #e5e7eb; /* off-white, lebih soft */
  margin-top: 8px;
}

.modal-content h5 {
  font-size: 1.1rem;
  margin-bottom: 10px;
  color: #ffffff;
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
