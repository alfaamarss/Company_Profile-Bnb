<template>
  <section class="project-section text-white">
    <div class="container">
      <div class="text-center mb-5">
        <h3 class="fw-bold">Proyek yang Telah Kami Selesaikan</h3>
        <p class="project-subtitle">Beberapa proyek epoxy dan waterproofing yang telah kami tangani</p>
      </div>

      <Swiper
        :modules="[Navigation, Pagination, Autoplay]"
        :slides-per-view="1"
        :space-between="24"
        :loop="true"
        :autoplay="{ delay: 3500 }"
        :pagination="{ clickable: true }"
        :breakpoints="{
          768: { slidesPerView: 2 },
          1200: { slidesPerView: 3 },
        }"
        class="project-swiper"
      >
        <SwiperSlide v-for="project in proyek" :key="project.title">
          <div class="project-card">
            <!-- IMAGE -->
            <div class="project-img">
              <img :src="project.image" :alt="project.title" />
            </div>

            <!-- CONTENT -->
            <div class="project-body">
              <h6 class="fw-bold">{{ project.title }}</h6>
              <p class="project-desc">{{ project.desc }}</p>

              <div class="project-meta">
                <span>📍 {{ project.location }}</span>
                <span>🏗️ {{ project.type }}</span>
              </div>
            </div>
          </div>
        </SwiperSlide>
      </Swiper>
    </div>
  </section>
</template>

<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, Pagination, Autoplay } from "swiper/modules";

import "swiper/css";
import "swiper/css/pagination";
import "swiper/css/navigation";

import p1 from "../assets/proyek/proyek1.jpeg";
import p2 from "../assets/proyek/proyek2.jpeg";
import p3 from "../assets/proyek//proyek3.jpeg";
import p4 from "../assets/proyek/proyek4.jpeg";
const proyek = [
  {
    title: "Epoxy Flooring Pabrik",
    desc: "Pengerjaan epoxy lantai area produksi dengan standar industri.",
    location: "Bekasi",
    type: "Epoxy Flooring",
    image: p1,
  },
  {
    title: "Waterproofing Gedung",
    desc: "Waterproofing atap dan basement gedung perkantoran.",
    location: "Jakarta",
    type: "Waterproofing Membran",
    image: p2,
  },
  {
    title: "Floor Hardener Gudang",
    desc: "Pengerjaan floor hardener area gudang logistik.",
    location: "Tangerang",
    type: "Floor Hardener",
    image: p3,
  },
  {
    title: "Floor Hardener Gudang",
    desc: "Pengerjaan floor hardener area gudang logistik.",
    location: "Tangerang",
    type: "Floor Hardener",
    image: p4,
  },
];
</script>

<style scoped>
/* ================= SECTION ================= */
.project-section {
  background: linear-gradient(135deg, #f0f6ff, #eaf1fb);
  padding: 5rem 0;
  color: #1e293b;
}

.project-section h3 {
  color: #1e3c72;
  font-weight: 700;
}

.project-subtitle {
  max-width: 600px;
  margin: 0 auto;
  color: #475569;
  font-size: 0.95rem;
}

/* ================= SWIPER ================= */
.project-swiper {
  padding-bottom: 42px;
}

:deep(.swiper-slide) {
  display: flex;
  height: auto;
}

/* ================= CARD ================= */
.project-card {
  display: flex;
  flex-direction: column;
  flex: 1;
  height: 100%;

  border-radius: 20px;
  overflow: hidden;
  background: #ffffff;
  border: 1px solid #e5e7eb;

  box-shadow:
    0 10px 25px rgba(30, 60, 114, 0.12),
    0 4px 10px rgba(0, 0, 0, 0.04);

  transition:
    transform 0.35s ease,
    box-shadow 0.35s ease;
}

.project-card:hover {
  transform: translateY(-8px);
  box-shadow:
    0 22px 45px rgba(30, 60, 114, 0.22),
    0 10px 18px rgba(0, 0, 0, 0.08);
}

/* ================= IMAGE ================= */
.project-img {
  position: relative;
  height: 200px;
  flex-shrink: 0;
  overflow: hidden;
}

.project-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.45s ease;
}

.project-card:hover .project-img img {
  transform: scale(1.08);
}

/* OVERLAY HALUS */
.project-img::after {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 55%, rgba(0, 0, 0, 0.25));
}

/* ================= BODY ================= */
.project-body {
  padding: 22px;
  display: flex;
  flex-direction: column;
  flex: 1;
}

.project-body h6 {
  color: #1e3c72;
  font-weight: 700;
  font-size: 0.95rem;
  margin-bottom: 8px;

  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
  line-clamp: 2;
  overflow: hidden;
}

.project-desc {
  font-size: 0.9rem;
  color: #475569;
  line-height: 1.5;
  margin-bottom: 14px;

  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  line-clamp: 3;
  overflow: hidden;
}

/* META STAY BAWAH */
.project-meta {
  margin-top: auto;
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  font-size: 0.8rem;
  color: #64748b;
}
</style>
