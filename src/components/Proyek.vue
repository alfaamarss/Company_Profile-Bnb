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
              <span class="project-badge">Selesai</span>
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

import p1 from "../assets/proyek/Epoxy1.jpeg";
import p2 from "../assets/proyek/decorative.png";
import p3 from "../assets/proyek/epoxy.png";

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
    image: p3,
  },
];
</script>

<style scoped>
.project-section {
  background: linear-gradient(135deg, #1e3c72, #2a5298);
  padding: 5rem 0;
}

.project-subtitle {
  max-width: 600px;
  margin: 0 auto;
  color: rgba(255, 255, 255, 0.85);
  font-size: 0.95rem;
}

/* CARD */
.project-card {
  height: 100%;
  border-radius: 20px;
  overflow: hidden;
  background: rgba(255, 255, 255, 0.18);
  backdrop-filter: blur(18px);
  border: 1px solid rgba(255, 255, 255, 0.28);
  transition: all 0.35s ease;
}

.project-card:hover {
  transform: translateY(-10px);
  background: rgba(255, 255, 255, 0.25);
  box-shadow: 0 22px 45px rgba(0, 0, 0, 0.35);
}

/* IMAGE */
.project-img {
  position: relative;
  height: 200px;
  overflow: hidden;
}

.project-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.45s ease;
}

.project-card:hover .project-img img {
  transform: scale(1.1);
}

/* BADGE */
.project-badge {
  position: absolute;
  top: 14px;
  left: 14px;
  background: rgba(40, 167, 69, 0.9);
  padding: 6px 12px;
  font-size: 0.75rem;
  border-radius: 20px;
}

/* BODY */
.project-body {
  padding: 20px;
  color: #fff;
}

.project-desc {
  font-size: 0.9rem;
  margin-bottom: 12px;
  color: rgba(255, 255, 255, 0.9);
}

.project-meta {
  display: flex;
  gap: 12px;
  font-size: 0.8rem;
  opacity: 0.9;
}

.project-swiper {
  padding-bottom: 40px;
}

/* Pagination bullet */
:deep(.swiper-pagination-bullet) {
  background: rgba(255, 255, 255, 0.6);
  opacity: 1;
}

:deep(.swiper-pagination-bullet-active) {
  background: #ffffff;
}
</style>
