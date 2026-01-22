<template>
  <footer class="site-footer py-5 bg-primary text-white">
    <!-- Wave -->

    <div class="container">
      <div class="row g-4">
        <!-- Kiri: Info Perusahaan + Kontak + Sosial Media -->
        <div class="col-12 col-md-6 footer-section reveal fade-up">
          <!-- Info Perusahaan -->
          <h5>CV. Berkah Doa Bunda</h5>
          <p>Contractor Specialist Epoxy, Decorative Painting & Waterproofing. Memberikan layanan profesional dengan pengalaman bertahun-tahun.</p>

          <!-- Kontak + Sosial Media Sebaris -->
          <div class="d-flex flex-wrap align-items-start gap-5 mt-4">
            <!-- Kontak -->
            <ul class="list-unstyled mb-0 flex-shrink-0">
              <li>📍 Tangerang, Indonesia</li>
              <li>📧 info@berkahdoabunda.com</li>
              <li>📞 +62 812 3456 7890</li>
            </ul>

            <!-- Sosial Media -->
            <div class="d-flex flex-column gap-2 flex-shrink-0">
              <span class="fw-semibold">Sosial Media:</span>
              <div class="social-links d-flex gap-3">
                <a href="#" class="social-link">Facebook</a>
                <a href="#" class="social-link">Instagram</a>
                <a href="#" class="social-link">LinkedIn</a>
              </div>
            </div>
          </div>
        </div>

        <!-- Kanan: Maps -->
        <div class="col-12 col-md-6 footer-section reveal fade-up" style="transition-delay: 0.1s">
          <div class="footer-map">
            <iframe
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3966.047521393961!2d106.5766881!3d-6.2574705999999995!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e69fdb0d3b9c1c9%3A0x59198a5b7af88dd1!2sCV.%20BERKAH%20DOA%20BUNDA%20%5B%20GUDANG%20EPOXY%20DAN%20JASA%20EPOXY%20LANTAI%20TANGERANG%20%5D!5e0!3m2!1sid!2sid!4v1767043281935!5m2!1sid!2sid"
              class="map-iframe"
              allowfullscreen
              loading="lazy"
              referrerpolicy="no-referrer-when-downgrade"
            ></iframe>
          </div>
        </div>
      </div>

      <hr class="my-4 border-secondary" />

      <p class="text-center mb-0">&copy; {{ new Date().getFullYear() }} CV. Berkah Doa Bunda. All rights reserved.</p>
    </div>
  </footer>
</template>

<script setup lang="ts">
import { onMounted, nextTick } from "vue";

onMounted(() => {
  nextTick(() => {
    const footerSections = document.querySelectorAll(".footer-section");

    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add("visible");
          } else {
            entry.target.classList.remove("visible");
          }
        });
      },
      { threshold: 0.2 },
    );

    footerSections.forEach((el) => observer.observe(el));
  });
});
</script>

<style scoped>
.site-footer {
  position: relative;
  background: linear-gradient(135deg, #5dade2 0%, #2a5298 50%, #5dade2 100%);
  color: white;
  padding-top: 4rem;
  padding-bottom: 3rem;
  font-family: sans-serif;
  overflow: hidden;
}

.footer-wave {
  position: absolute;
  top: -1px;
  left: 0;
  width: 100%;
  height: 100px;
}

.footer-wave svg {
  display: block;
  width: 100%;
  height: 100%;
}

.footer-section h5,
.footer-section ul li,
.social-link {
  color: white;
}

.social-link {
  color: white;
  text-decoration: none;
  transition: color 0.3s;
}

.social-link:hover {
  color: #ffd700; /* Warna aksen cat/epoxy */
}

/* Footer Maps */
.footer-map iframe {
  width: 100%;
  height: 250px;
  border-radius: 12px;
  margin-top: 1rem;
  border: 0;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
}

/* Animasi scroll */
.reveal {
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.6s ease;
}

.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}

/* Separator line */
hr {
  border-color: rgba(255, 255, 255, 0.3);
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .footer-map iframe {
    height: 200px;
  }
}
</style>
