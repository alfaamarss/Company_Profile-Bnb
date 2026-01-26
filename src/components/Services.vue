<template>
  <section id="layanan" class="py-5">
    <div class="container">
      <h2 class="mb-4 text-center">layanan Kami</h2>

      <div class="layanan-scroll-wrapper">
        <div class="layanan-scroll d-flex gap-3">
          <div v-for="(layanan, index) in layananList" :key="index" class="layanan-card card text-center" @click="openlayanan(layanan)">
            <img :src="layanan.images[0]" class="img-fluid mb-2" />
            <h6 class="fw-bold">{{ layanan.title }}</h6>
            <p class="mb-0">{{ layanan.shortDesc }}</p>
          </div>
        </div>
      </div>
    </div>

    <!-- MODAL GLASS -->
    <div v-if="selectedlayanan" class="modal-overlay" @click.self="closelayanan">
      <div class="modal-content glass-modal">
        <img :src="selectedlayanan.images[currentImage]" class="img-fluid mb-3 rounded" />

        <!-- NAV IMAGE -->
        <div v-if="selectedlayanan.images.length > 1" class="d-flex justify-content-between mb-3">
          <button class="btn btn-light btn-sm" @click="prevImage">‹</button>
          <button class="btn btn-light btn-sm" @click="nextImage">›</button>
        </div>

        <h5 class="fw-bold mb-2">{{ selectedlayanan.title }}</h5>
        <p>{{ selectedlayanan.fullDesc }}</p>

        <button class="btn btn-primary mt-3" @click="closelayanan">Tutup</button>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from "vue";

/* ===== TYPE ===== */
interface layanan {
  title: string;
  shortDesc: string;
  fullDesc: string;
  images: string[];
}

/* ===== IMAGES ===== */

import waterproofingImg from "../assets/waterproofing.png";
import roadMarkingImg from "../assets/road-marking.png";
import protectiveImg from "../assets/protective.png";
import sportFlooringImg from "../assets/sport-flooring.png";
import decorativeImg from "../assets/decorative.png";
import floorHardenerImg from "../assets/floor-hardener.png";
import membranImg from "../assets/membran.png";

/* ===== DATA ===== */
const layananList: layanan[] = [
  {
    title: "Pengecatan Lapangan Indoor & Outdoor",
    shortDesc: "Pengecatan lapangan berkualitas dengan metode Plexipave",
    fullDesc:
      "layanan jasa pengecatan lapangan kami dikerjakan dengan standar kualitas tinggi. Proses pengecatan menggunakan metode Plexipave yang terbukti tahan retak serta mampu mencegah terjadinya genangan air. layanan ini sangat ideal bagi Anda yang sedang merencanakan pembangunan maupun renovasi lapangan olahraga indoor maupun outdoor.",
    images: [sportFlooringImg],
  },
  {
    title: "Pengecatan Pabrik & Gudang",
    shortDesc: "Lantai industri kuat, rapi, dan tahan lama",
    fullDesc: "layanan pengecatan pabrik dan gudang dengan sistem epoxy berkualitas tinggi untuk menghasilkan lantai yang kuat, rapi, tahan beban berat, serta mudah dalam perawatan jangka panjang.",
    images: [protectiveImg],
  },
  {
    title: "Pengecatan Marka Jalan / Road Marking",
    shortDesc: "Garis marka jalan jelas dan presisi",
    fullDesc: "Pengecatan marka jalan menggunakan material berkualitas tinggi yang menghasilkan garis jelas, presisi, serta tahan aus terhadap lalu lintas dan kondisi cuaca ekstrem.",
    images: [roadMarkingImg],
  },
  {
    title: "Pengecatan Jembatan",
    shortDesc: "Perlindungan struktur jembatan",
    fullDesc: "Pengecatan jembatan dengan sistem pelapisan khusus untuk melindungi struktur dari korosi, cuaca ekstrem, dan memperpanjang usia pakai konstruksi.",
    images: [protectiveImg],
  },
  {
    title: "Pengecatan Protective Coating",
    shortDesc: "Perlindungan maksimal dari korosi dan cuaca",
    fullDesc: "layanan protective coating untuk melindungi permukaan logam maupun beton dari korosi, bahan kimia, serta paparan cuaca ekstrem.",
    images: [protectiveImg],
  },
  {
    title: "Pengecatan Waterproofing",
    shortDesc: "Solusi anti bocor untuk bangunan",
    fullDesc: "layanan waterproofing profesional untuk mencegah kebocoran pada atap, dak, basement, dan area bangunan lainnya.",
    images: [waterproofingImg],
  },
  {
    title: "Jasa Decorative Flooring",
    shortDesc: "Finishing lantai estetik dan modern",
    fullDesc: "Jasa decorative flooring dengan berbagai pilihan desain untuk memberikan tampilan lantai yang estetik, modern, dan bernilai tambah pada bangunan Anda.",
    images: [decorativeImg],
  },
];

/* ===== MODAL ===== */
const selectedlayanan = ref<layanan | null>(null);
const currentImage = ref(0);

const openlayanan = (layanan: layanan) => {
  selectedlayanan.value = layanan;
  currentImage.value = 0;
};

const closelayanan = () => {
  selectedlayanan.value = null;
};

const nextImage = () => {
  if (!selectedlayanan.value) return;
  currentImage.value = (currentImage.value + 1) % selectedlayanan.value.images.length;
};

const prevImage = () => {
  if (!selectedlayanan.value) return;
  currentImage.value = (currentImage.value - 1 + selectedlayanan.value.images.length) % selectedlayanan.value.images.length;
};
</script>

<style scoped>
/* ===================== ROOT SECTION ===================== */
#layanan {
  background: linear-gradient(135deg, #f5f9ff, #e8f0fb);
  color: #0f172a;
}

/* ===================== TITLE ===================== */
#layanan h2 {
  font-weight: 700;
  letter-spacing: 0.4px;
  color: #0b3a6e;
}

/* ===================== SCROLL WRAPPER ===================== */
.layanan-scroll-wrapper {
  overflow-x: auto;
  padding: 8px 0 16px;
  scrollbar-width: none;
}
.layanan-scroll-wrapper::-webkit-scrollbar {
  display: none;
}

.layanan-scroll {
  display: flex;
  gap: 20px;
  padding: 4px 2px;
}

/* ===================== CARD ===================== */
.layanan-card {
  min-width: 200px;
  max-width: 200px;
  padding: 14px;
  border-radius: 18px;

  background: rgba(255, 255, 255, 0.72);
  backdrop-filter: blur(14px);
  border: 1px solid rgba(15, 23, 42, 0.08);

  color: #0f172a;
  cursor: pointer;

  transition:
    transform 0.35s ease,
    box-shadow 0.35s ease;
}

.layanan-card:hover {
  transform: translateY(-6px);
  box-shadow:
    0 18px 34px rgba(15, 23, 42, 0.25),
    inset 0 1px 0 rgba(255, 255, 255, 0.85);
}

/* ===================== IMAGE ===================== */
.layanan-card img {
  width: 100%;
  height: 120px;
  object-fit: cover;
  border-radius: 14px;
  margin-bottom: 10px;
}

/* ===================== CARD TEXT ===================== */
.layanan-card h6 {
  font-size: 0.95rem;
  font-weight: 700;
  margin-bottom: 4px;
  color: #0b3a6e;
}

.layanan-card p {
  font-size: 0.8rem;
  margin: 0;
  color: #475569;
}

/* ===================== MODAL OVERLAY ===================== */
.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(10, 20, 40, 0.6);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
  padding: 16px;
}

/* ===================== MODAL CONTENT ===================== */
.modal-content {
  max-width: 480px;
  width: 100%;
  padding: 24px;

  background: rgba(255, 255, 255, 0.88);
  backdrop-filter: blur(18px);
  border-radius: 24px;

  border: 1px solid rgba(15, 23, 42, 0.12);

  box-shadow:
    0 25px 55px rgba(15, 23, 42, 0.35),
    inset 0 1px 0 rgba(255, 255, 255, 0.9);

  color: #0f172a;
  text-align: center;

  animation: modalIn 0.35s ease;
}

/* ===================== MODAL IMAGE ===================== */
.modal-content img {
  max-height: 240px;
  width: 100%;
  object-fit: cover;
  border-radius: 18px;
}

/* ===================== MODAL TEXT ===================== */
.modal-content h5 {
  font-size: 1.1rem;
  font-weight: 700;
  margin: 12px 0 8px;
  color: #0b3a6e;
}

.modal-content p {
  font-size: 0.95rem;
  line-height: 1.65;
  letter-spacing: 0.2px;
  color: #475569;
  margin-top: 8px;
}

/* ===================== BUTTON ===================== */
.modal-content .btn {
  border-radius: 999px;
  font-weight: 600;
}

/* ===================== ANIMATION ===================== */
@keyframes modalIn {
  from {
    transform: translateY(18px) scale(0.97);
    opacity: 0;
  }
  to {
    transform: translateY(0) scale(1);
    opacity: 1;
  }
}
</style>
