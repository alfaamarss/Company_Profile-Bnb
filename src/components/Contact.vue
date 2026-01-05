<template>
  <section id="kontak" class="py-5" style="background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2)">
    <div class="container">
      <h2 class="mb-5 text-center text-white reveal-title">Kontak Kami</h2>

      <div class="glass-card mx-auto p-4 shadow-lg reveal">
        <div class="row align-items-center g-4">
          <!-- KONTEN KONTAK -->
          <div class="col-md-6">
            <ul class="list-group list-group-flush">
              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span class="d-flex align-items-center gap-2"> 📞 Telepon </span>
                <a href="tel:085212714789">0852-1271-4789</a>
              </li>

              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span class="d-flex align-items-center gap-2"> ✉️ Email </span>
                <a href="mailto:cv.berkahdoabunda@gmail.com"> cv.berkahdoabunda@gmail.com </a>
              </li>

              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span><img :src="wa" class="icon" /> WhatsApp</span>
                <a href="https://wa.me/6285212714789" target="_blank" class="btn btn-success btn-sm"> Chat Sekarang </a>
              </li>

              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span><img :src="tokopedia" class="icon" /> Tokopedia</span>
                <a href="#" class="btn btn-warning btn-sm">Kunjungi</a>
              </li>

              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span><img :src="shopee" class="icon" /> Shopee</span>
                <a href="#" class="btn btn-danger btn-sm">Kunjungi</a>
              </li>
            </ul>
          </div>

          <!-- LOGO -->
          <div class="col-md-6 text-center reveal delay">
            <img :src="logo" alt="CV Berkah Doa Bunda" class="img-fluid logo" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { onMounted } from "vue";

import logo from "../assets/logo.png";
import wa from "../assets/wa.png";
import tokopedia from "../assets/tokopedia.jpeg";
import shopee from "../assets/shopee.png";

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("active");
        }
      });
    },
    { threshold: 0.25 }
  );

  document.querySelectorAll(".reveal, .reveal-title").forEach((el) => {
    observer.observe(el);
  });
});
</script>

<style scoped>
/* ===================== GLASS CARD ===================== */
.glass-card {
  background: rgba(255, 255, 255, 0.12);
  backdrop-filter: blur(15px);
  border-radius: 22px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  color: white;
}

/* ===================== LIST ===================== */
.list-group-item {
  background: transparent;
  border: none;
  color: white;
}

.list-group-item a {
  color: white;
  text-decoration: none;
}

/* ===================== ICON ===================== */
.icon {
  width: 22px;
  height: 22px;
}

/* ===================== LOGO ===================== */
.logo {
  max-height: 260px;
  border-radius: 20px;
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
}

/* ===================== SCROLL ANIMATION ===================== */
.reveal {
  opacity: 0;
  transform: translateY(70px) scale(0.95);
  transition: all 1s cubic-bezier(0.19, 1, 0.22, 1);
}

.reveal-title {
  opacity: 0;
  transform: translateY(40px);
  transition: all 0.8s ease;
}

.active {
  opacity: 1;
  transform: translateY(0) scale(1);
}

.delay {
  transition-delay: 0.25s;
}
</style>
