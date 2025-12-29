<template>
  <section class="hero-section">
    <img :src="heroImage" class="hero-bg" alt="Hero Image" />

    <div class="hero-overlay">
      <div class="hero-card">
        <!-- Kiri: Teks -->
        <div class="hero-text">
          <h1>CV. Berkah Doa Bunda</h1>
          <p>Contractor Specialist Epoxy, Decorative Painting & Waterproofing</p>
        </div>

        <!-- Kanan: Logo -->
        <div class="hero-logo">
          <img :src="logo" alt="Logo" />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import heroImage from "../assets/slide1.png";
import logo from "../assets/logo.png";
</script>
<style scoped>
.hero-section {
  position: relative;
  height: 100vh;
  overflow: hidden;
}

/* Background */
.hero-bg {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Overlay */
.hero-overlay {
  position: relative;
  z-index: 2;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0, 0, 0, 0.45);
}

/* Glass Card */
.hero-card {
  display: flex;
  align-items: center;
  gap: 3rem;
  padding: 3rem 4rem;
  border-radius: 20px;

  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);

  box-shadow: 0 15px 40px rgba(0, 0, 0, 0.45);
  color: white;
  max-width: 900px;
  width: 90%;
}

/* Text */
.hero-text h1 {
  font-size: clamp(2rem, 4vw, 3.2rem);
  font-weight: 700;
  margin-bottom: 0.75rem;
}

.hero-text p {
  font-size: clamp(1rem, 2vw, 1.3rem);
  max-width: 420px;
  line-height: 1.6;
}

/* Logo */
.hero-logo img {
  width: 160px;
  max-width: 100%;
  height: auto;
  filter: drop-shadow(0 5px 10px rgba(0, 0, 0, 0.5));
}

/* ================= MOBILE ================= */
@media (max-width: 768px) {
  .hero-section {
    height: 80vh;
  }

  .hero-card {
    flex-direction: column;
    text-align: center;
    gap: 1.5rem;
    padding: 2rem 1.5rem;
  }

  .hero-text p {
    max-width: 100%;
  }

  .hero-logo img {
    width: 110px;
  }
}
</style>
