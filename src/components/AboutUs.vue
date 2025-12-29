<template>
  <section id="tentang-kami" class="py-5">
    <div class="container">
      <h2 class="mb-5 text-center">Tentang Kami</h2>

      <!-- Tambah class reveal & ref -->
      <div class="row align-items-center reveal" ref="aboutSection">
        <!-- Kiri: Card dengan teks -->
        <div class="col-lg-6 mb-4 mb-lg-0 fade-left">
          <div class="card shadow-sm h-100">
            <div class="card-body">
              <h5 class="card-title fw-bold mb-3">CV. Berkah Doa Bunda</h5>
              <p class="card-text">
                CV. BERKAH DOA BUNDA merupakan salah satu perusahaan di Tangerang yang bergerak di penyedia layanan Jasa Epoxy Flooring berkualitas dan berpengalaman dalam mengerjakan aplikasian Flooring Coating (Pengecatan) Decorative,
                Protective, Waterproofing, Manufacturing & Trading. Kami memiliki sistem dan prosedur yang memenuhi standar industri dan juga mempekerjakan staf profesional yang ahli dan berpengalaman dalam bidangnya.
              </p>
              <p class="card-text">
                Kepuasan pelanggan menjadi prioritas utama kami. Kami menggunakan produk cat epoxy lantai yang kami produksi sendiri di pabrik, dan juga produk dari Propan, Jotun, sesuai spesifikasi klien. Kami berkomitmen memberikan
                pelayanan terbaik agar hasil kerja memuaskan.
              </p>
            </div>
          </div>
        </div>

        <!-- Kanan: Gambar Slider -->
        <div class="col-lg-6 fade-right">
          <div class="about-slider">
            <img :src="slides[currentSlide]" class="img-fluid rounded shadow-sm slide-image" :class="{ hide: isAnimating }" />

            <!-- Arrow -->
            <button class="arrow prev" @click="prevSlide">‹</button>
            <button class="arrow next" @click="nextSlide">›</button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { onMounted, ref, onBeforeUnmount } from "vue";

import slide1 from "../assets/slide1.png";
import slide2 from "../assets/slide2.png";
import slide3 from "../assets/slide3.png";

const aboutSection = ref<HTMLElement | null>(null);

const slides = [slide1, slide2, slide3];
const currentSlide = ref(0);
const isAnimating = ref(false);

const animateSlide = (callback: () => void) => {
  isAnimating.value = true;

  setTimeout(() => {
    callback();
    setTimeout(() => {
      isAnimating.value = false;
    }, 50);
  }, 300);
};

let interval: number;

const nextSlide = () => {
  animateSlide(() => {
    currentSlide.value = (currentSlide.value + 1) % slides.length;
  });
};

const prevSlide = () => {
  animateSlide(() => {
    currentSlide.value = (currentSlide.value - 1 + slides.length) % slides.length;
  });
};

onMounted(() => {
  interval = window.setInterval(nextSlide, 3000);

  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        entry.target.classList.toggle("active", entry.isIntersecting);
      });
    },
    { threshold: 0.3 }
  );

  if (aboutSection.value) observer.observe(aboutSection.value);
});

onBeforeUnmount(() => {
  clearInterval(interval);
});
</script>

<style scoped>
/* Section background */
#tentang-kami {
  padding: 2rem 0;
  background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
  color: white;
}

/* Card glass effect */
.card {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border-radius: 16px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  color: white;
}

.card-body p {
  line-height: 1.6;
  color: white;
}

.card-title {
  color: white;
}

/* ===== ANIMASI SCROLL ===== */

.reveal .fade-left,
.reveal .fade-right {
  opacity: 0;
  transform: translateX(0);
  transition: all 0.8s ease;
}

@media (min-width: 768px) {
  .reveal .fade-left {
    transform: translateX(-60px);
  }

  .reveal .fade-right {
    transform: translateX(60px);
  }
}

.reveal.active .fade-left,
.reveal.active .fade-right {
  opacity: 1;
  transform: translateX(0);
}

.about-slider {
  position: relative;
  overflow: hidden;
  border-radius: 16px; /* agar slider juga terlihat rounded */
}

/* Slide image */
.slide-image {
  width: 100%;
  transition: opacity 0.6s ease, transform 0.6s ease;
  border-radius: 16px;
}

.slide-image.hide {
  opacity: 0;
  transform: scale(1.05);
}

/* ===== SLIDER ARROW ===== */

/* ===== SLIDER ARROW ===== */
.arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  font-size: 42px;
  font-weight: 300;
  color: white;
  background: none; /* hilangkan lingkaran */
  border: none;
  cursor: pointer;
  opacity: 0.6;
  transition: all 0.3s ease;
  user-select: none;
  z-index: 5;
}

.arrow:hover {
  opacity: 1;
  transform: translateY(-50%) scale(1.15);
}

.prev {
  left: 12px;
}
.next {
  right: 12px;
}

/* Mobile adjustments */
@media (max-width: 768px) {
  .arrow {
    font-size: 32px;
    width: auto;
    height: auto;
  }
}

.arrow:hover {
  opacity: 1;
  transform: translateY(-50%) scale(1.15);
}

.prev {
  left: 12px;
}
.next {
  right: 12px;
}

/* ================= MOBILE COMPACT MODE ================= */
@media (max-width: 768px) {
  #tentang-kami {
    padding-top: 3rem;
    padding-bottom: 3rem;
  }

  #tentang-kami h2 {
    margin-bottom: 2rem;
    font-size: 1.8rem;
  }

  .card-body {
    padding: 1.25rem;
  }

  .card-body p {
    font-size: 0.95rem;
    line-height: 1.45;
  }

  /* Potong teks supaya ga kepanjangan */
  .card-body p:last-child {
    display: none;
  }

  .about-slider {
    margin-top: 1rem;
  }

  .slide-image {
    max-height: 240px;
    object-fit: cover;
  }

  .arrow {
    font-size: 32px;
    width: 36px;
    height: 36px;
  }
}
</style>
