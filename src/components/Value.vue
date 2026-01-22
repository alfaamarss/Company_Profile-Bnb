<template>
  <section class="vp-section text-white">
    <div class="container text-center">
      <h3 class="fw-bold mb-2">Kenapa Memilih Kami?</h3>
      <p class="vp-subtitle mb-5">Solusi lantai & waterproofing profesional dan terpercaya</p>

      <div class="row g-4 justify-content-center">
        <div class="col-12 col-md-6 col-lg-4" v-for="item in items" :key="item.title">
          <div class="vp-card">
            <!-- DECORATIVE -->
            <img class="vp-decorative" :src="decorative" alt="" />

            <!-- IMAGE (ATAS) -->
            <div class="vp-img-wrapper">
              <img :src="item.image" :alt="item.title" />
            </div>

            <!-- CONTENT (BAWAH) -->
            <div class="vp-card-body">
              <h6 class="fw-bold">{{ item.title }}</h6>
              <p>{{ item.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import decorative from "../assets/value/decorative.png";
import epoxy from "../assets/value/epoxy.png";
import floorHardener from "../assets/value/Epoxy1.jpeg";
import membran from "../assets/value/membran.png";

const items = [
  {
    title: "Berpengalaman",
    desc: "Menangani berbagai proyek epoxy & waterproofing di sektor industri dan komersial.",
    image: epoxy,
  },
  {
    title: "Material Berkualitas",
    desc: "Menggunakan material produksi sendiri dan brand ternama dengan standar tinggi.",
    image: floorHardener,
  },
  {
    title: "Tim Profesional",
    desc: "Didukung tenaga ahli yang berpengalaman dan bersertifikasi.",

    image: membran,
  },
];
</script>

<style scoped>
.vp-section {
  background: linear-gradient(135deg, #1e3c72, #2a5298);
  padding: 5rem 0;
}

.vp-subtitle {
  max-width: 600px;
  margin: 0 auto;
  color: rgba(255, 255, 255, 0.85);
  font-size: 0.95rem;
}

/* CARD */
.vp-card {
  position: relative;
  height: 100%;
  border-radius: 22px;
  overflow: hidden;
  background: rgba(255, 255, 255, 0.18);
  backdrop-filter: blur(18px);
  border: 1px solid rgba(255, 255, 255, 0.28);
  transition: all 0.35s ease;
}

.vp-card:hover {
  transform: translateY(-10px);
  background: rgba(255, 255, 255, 0.26);
  box-shadow: 0 22px 50px rgba(0, 0, 0, 0.35);
}

/* DECORATIVE */
.vp-decorative {
  position: absolute;
  top: -40px;
  right: -40px;
  width: 130px;
  opacity: 0.18;
  pointer-events: none;
  z-index: 1;
}

/* IMAGE */
/* IMAGE */
.vp-img-wrapper {
  position: relative;
  z-index: 2;
  width: 100%;
  height: 200px;
  overflow: hidden;
}

.vp-img-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: cover; /* PENTING */
  transition: transform 0.45s ease;
}

.vp-card:hover .vp-img-wrapper img {
  transform: scale(1.1);
}

/* BODY */
.vp-card-body {
  position: relative;
  z-index: 2;
  padding: 22px;
  color: #fff;
}

.vp-card-body p {
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.9);
}
</style>
