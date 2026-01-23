<template>
  <section class="vp-section">
    <div class="container text-center">
      <h3 class="fw-bold mb-2">Kenapa Memilih Kami?</h3>
      <p class="vp-subtitle mb-4">Solusi lantai & waterproofing profesional dan terpercaya</p>

      <!-- SLIDER WRAPPER -->
      <div class="vp-slider">
        <div class="vp-track">
          <div class="vp-slide" v-for="item in items" :key="item.title">
            <div class="vp-card">
              <!-- IMAGE -->
              <div class="vp-img-wrapper">
                <img :src="item.image" :alt="item.title" />
                <div class="vp-img-overlay"></div>
              </div>

              <!-- CONTENT -->
              <div class="vp-card-body">
                <h6 class="fw-bold">{{ item.title }}</h6>
                <p>{{ item.desc }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- DOTS -->
      <div class="vp-dots d-md-none">
        <span v-for="n in items.length" :key="n"></span>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import Value3 from "../assets/value/Value3.jpeg";
import Value1 from "../assets/value/Value1.jpeg";
import Value4 from "../assets/value/Value4.jpeg";

const items = [
  {
    title: "Berpengalaman",
    desc: "Menangani berbagai proyek epoxy & waterproofing di sektor industri dan komersial.",
    image: Value3,
  },
  {
    title: "Material Berkualitas",
    desc: "Menggunakan material produksi sendiri dan brand ternama dengan standar tinggi.",
    image: Value1,
  },
  {
    title: "Tim Profesional",
    desc: "Didukung tenaga ahli yang berpengalaman dan bersertifikasi.",
    image: Value4,
  },
];
</script>

<style>
.vp-section {
  position: relative;
  background: linear-gradient(135deg, #f0f6ff, #eaf1fb);
  padding: 5rem 0;
  color: #1e293b;
} /* GARIS ATAS */
.vp-section::before {
  content: "";
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: min(420px, 80%);
  height: 3px;
  background: linear-gradient(90deg, #1e3c72, #5dade2);
  border-radius: 999px;
} /* TEXT */
.vp-section h3 {
  color: #1e3c72;
}
.vp-subtitle {
  color: #475569;
  font-size: 0.95rem;
} /* =====
SLIDER ===== */
.vp-slider {
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  -webkit-overflow-scrolling: touch;
}
.vp-track {
  display: flex;
  gap: 1.2rem;
} /* MOBILE SLIDE */
.vp-slide {
  min-width: 85%;
  scroll-snap-align: center;
} /*
DESKTOP GRID */
@media (min-width: 768px) {
  .vp-slider {
    overflow: visible;
  }
  .vp-track {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
  }
  .vp-slide {
    min-width: auto;
  }
} /* ===== CARD ===== */
.vp-card {
  position: relative;
  height: 100%;
  border-radius: 22px;
  overflow: hidden;
  background: #fff;
  border: 1px solid #e5e7eb;
  box-shadow: 0 14px 34px rgba(30, 60, 114, 0.12);
  transition: all 0.35s ease;
}
.vp-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 22px 45px rgba(30, 60, 114, 0.18);
} /* DECORATIVE */
.vp-decorative {
  position: absolute;
  top: -40px;
  right: -40px;
  width: 120px;
  opacity: 0.08;
  pointer-events: none;
} /* IMAGE */
.vp-img-wrapper {
  position: relative;
  height: 200px;
  overflow: hidden;
}
.vp-img-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s ease;
}
.vp-card:hover img {
  transform: scale(1.1);
} /* OVERLAY */
.vp-img-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 40%, rgba(0, 0, 0, 0.35));
} /* BODY */
.vp-card-body {
  padding: 22px;
}
.vp-card-body h6 {
  color: #1e3c72;
}
.vp-card-body p {
  font-size: 0.9rem;
  color: #475569;
  line-height: 1.5;
} /* DOTS */
.vp-dots {
  display: flex;
  justify-content: center;
  gap: 6px;
  margin-top: 14px;
}
.vp-dots span {
  width: 8px;
  height: 8px;
  background: #cbd5e1;
  border-radius: 50%;
}
</style>
