<template>
  <section id="why-us" class="py-5">
    <div class="container">
      <h2 class="mb-5 text-center text-white">Kenapa Pilih Kami?</h2>

      <div class="row g-4 reveal" ref="whySection">
        <div v-for="(item, index) in reasons" :key="index" class="col-md-6 col-lg-3 fade-up">
          <div class="card h-100 why-card">
            <!-- IMAGE -->
            <div class="card-img-top-wrapper">
              <img :src="item.icon" alt="why-us" />
            </div>

            <!-- CONTENT -->
            <div class="card-body text-center">
              <h5 class="fw-bold mb-2">{{ item.title }}</h5>
              <p class="mb-0">{{ item.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";

/* IMAGES */
import epoxyIcon from "../assets/service/epoxy.png";
import decorativeIcon from "../assets/service/decorative.png";
import decorativeJpgIcon from "../assets/service/decorative.jpeg";
import floorHardenerIcon from "../assets/service/floor-hardener.png";

const whySection = ref<HTMLElement | null>(null);

const reasons = [
  {
    icon: epoxyIcon,
    title: "Tenaga Berpengalaman",
    desc: "Didukung tenaga profesional berpengalaman dalam pengerjaan epoxy dan flooring.",
  },
  {
    icon: decorativeIcon,
    title: "Hasil Rapi & Estetis",
    desc: "Pengerjaan detail dengan hasil rapi dan tampilan lantai yang estetis.",
  },
  {
    icon: decorativeJpgIcon,
    title: "Material Berkualitas",
    desc: "Menggunakan material pilihan sesuai kebutuhan dan spesifikasi klien.",
  },
  {
    icon: floorHardenerIcon,
    title: "Standar Industri",
    desc: "Proses kerja mengikuti SOP dan standar keselamatan kerja industri.",
  },
];

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        entry.target.classList.toggle("active", entry.isIntersecting);
      });
    },
    { threshold: 0.3 }
  );

  if (whySection.value) observer.observe(whySection.value);
});
</script>

<style scoped>
/* SECTION */
#why-us {
  background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
  color: white;
}

/* CARD */
.why-card {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  overflow: hidden;
  border: 1px solid rgba(255, 255, 255, 0.3);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  transition: 0.3s ease;
}

.why-card:hover {
  transform: translateY(-6px) scale(1.03);
}

/* IMAGE FULL SETENGAH ATAS */
.card-img-top-wrapper {
  height: 140px; /* SETENGAH CARD */
  overflow: hidden;
}

.card-img-top-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: cover; /* FULL & RAPI */
}

/* BODY */
.card-body {
  padding: 1.25rem;
}

.card-body {
  color: #ffffff; /* PUTIH SOLID */
}

.card-body p {
  color: rgba(255, 255, 255, 0.85); /* sedikit soft tapi tetep putih */
}

/* SCROLL ANIMATION */
.reveal .fade-up {
  opacity: 0;
  transform: translateY(40px);
  transition: 0.8s ease;
}

.reveal.active .fade-up {
  opacity: 1;
  transform: translateY(0);
}

/* MOBILE */
@media (max-width: 768px) {
  .card-img-top-wrapper {
    height: 120px;
  }
}
</style>
