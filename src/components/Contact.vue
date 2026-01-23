<template>
  <section id="kontak" class="kontak-section py-5">
    <div class="container">
      <h2 class="mb-5 text-center reveal-title">Kontak Kami</h2>

      <div class="glass-card mx-auto p-4 shadow-lg reveal">
        <div class="row align-items-center g-4">
          <!-- KONTEN KONTAK -->
          <div class="col-md-6">
            <ul class="list-group list-group-flush">
              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span class="d-flex align-items-center gap-2">📞 Telepon</span>
                <a href="tel:085212714789">0811-1185-2220</a>
              </li>

              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span class="d-flex align-items-center gap-2">✉️ Email</span>
                <a href="mailto:cv.berkahdoabunda@gmail.com"> cv.berkahdoabunda@gmail.com </a>
              </li>

              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span><img :src="wa" class="icon" /> WhatsApp</span>
                <a href="https://wa.me/6281111852220" target="_blank" class="btn btn-success btn-sm"> Chat Sekarang </a>
              </li>

              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span><img :src="tokopedia" class="icon" /> Tokopedia</span>
                <a href="https://tk.tokopedia.com/ZS5mFRdQB/" class="btn btn-warning btn-sm"> Kunjungi </a>
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
import tokopedia from "../assets/tokopedia.png";
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
    { threshold: 0.25 },
  );

  document.querySelectorAll(".reveal, .reveal-title").forEach((el) => {
    observer.observe(el);
  });
});
</script>

<style scoped>
/* ===================== SECTION ===================== */
.kontak-section {
  position: relative;
  background: linear-gradient(135deg, #f0f6ff, #dbeafe);
  overflow: hidden;
}

/* GARIS PEMISAH ATAS */
.kontak-section::before {
  content: "";
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: min(420px, 80%);
  height: 3px;
  background: linear-gradient(90deg, #1e3c72, #5dade2);
  border-radius: 999px;
}

/* ===================== GLASS CARD ===================== */
.glass-card {
  max-width: 900px;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(8px);

  border-radius: 24px;
  border: 1px solid #e5e7eb;
  color: #1e293b;

  box-shadow:
    0 20px 45px rgba(30, 60, 114, 0.18),
    0 8px 18px rgba(0, 0, 0, 0.06);
}

/* ===================== LIST ===================== */
.list-group-item {
  background: transparent;
  border: none;
  padding: 14px 0;
  font-size: 0.95rem;
  color: #334155;
}

.list-group-item:not(:last-child) {
  border-bottom: 1px solid #e5e7eb;
}

.list-group-item a {
  color: #1e3c72;
  font-weight: 600;
  text-decoration: none;
}

.list-group-item a:hover {
  text-decoration: underline;
}

/* ===================== ICON ===================== */
.icon {
  width: 22px;
  height: 22px;
  object-fit: contain;
}

/* ===================== BUTTON ===================== */
.btn {
  border-radius: 999px;
  font-size: 0.75rem;
  padding: 6px 14px;
}

/* ===================== LOGO ===================== */
.logo {
  max-height: 240px;
  border-radius: 18px;
  background: #ffffff;
  padding: 12px;

  box-shadow:
    0 18px 35px rgba(30, 60, 114, 0.22),
    0 6px 14px rgba(0, 0, 0, 0.08);
}

/* ===================== SCROLL ANIMATION ===================== */
.reveal {
  opacity: 0;
  transform: translateY(60px) scale(0.96);
  transition: all 0.9s cubic-bezier(0.19, 1, 0.22, 1);
}

.reveal-title {
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.7s ease;
}

.active {
  opacity: 1;
  transform: translateY(0) scale(1);
}

.delay {
  transition-delay: 0.25s;
}
</style>
