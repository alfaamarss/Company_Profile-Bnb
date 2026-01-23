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
              <li>📍 depan smpn 2, Sukabakti, Kec. Curug, Kabupaten Tangerang, Banten 15810</li>
              <li>📧 cv.berkahdoabunda@gmail.com</li>
            </ul>

            <!-- Sosial Media -->
            <div class="d-flex flex-column gap-2 flex-shrink-0">
              <span class="fw-semibold">Sosial Media:</span>

              <div class="social-links d-flex gap-3">
                <!-- Facebook -->
                <a href="https://www.facebook.com/share/1DE5NAHN2t/?mibextid=wwXIfr" class="social-link" aria-label="Facebook">
                  <svg width="22" height="22" viewBox="0 0 24 24" fill="currentColor">
                    <path d="M22 12a10 10 0 1 0-11.5 9.9v-7h-2v-2.9h2V9.8c0-2 1.2-3.1 3-3.1.9 0 1.8.1 1.8.1v2h-1c-1 0-1.3.6-1.3 1.2v1.8h2.2l-.4 2.9h-1.8v7A10 10 0 0 0 22 12z" />
                  </svg>
                </a>

                <!-- Instagram -->
                <a href="https://www.instagram.com/bdb_catepoxy?igsh=YXkxbzg5enlndG9p&utm_source=qr" class="social-link" aria-label="Instagram">
                  <svg width="22" height="22" viewBox="0 0 24 24" fill="currentColor">
                    <path
                      d="M7 2C4.2 2 2 4.2 2 7v10c0 2.8 2.2 5 5 5h10c2.8 0 5-2.2 5-5V7c0-2.8-2.2-5-5-5H7zm10 2c1.7 0 3 1.3 3 3v10c0 1.7-1.3 3-3 3H7c-1.7 0-3-1.3-3-3V7c0-1.7 1.3-3 3-3h10zm-5 3a5 5 0 1 0 0 10 5 5 0 0 0 0-10zm0 2a3 3 0 1 1 0 6 3 3 0 0 1 0-6zm4.5-.8a1.1 1.1 0 1 0 0 2.2 1.1 1.1 0 0 0 0-2.2z"
                    />
                  </svg>
                </a>

                <!-- LinkedIn -->
                <a href="https://www.linkedin.com/in/cv-berkah-doa-bunda-a29b27397/?locale=in_ID" class="social-link" aria-label="LinkedIn">
                  <svg width="22" height="22" viewBox="0 0 24 24" fill="currentColor">
                    <path d="M4.98 3.5A2.5 2.5 0 1 0 5 8.5a2.5 2.5 0 0 0-.02-5zM3 9h4v12H3V9zm7 0h3.8v1.7h.1c.5-.9 1.7-1.9 3.6-1.9 3.9 0 4.6 2.5 4.6 5.8V21h-4v-5.6c0-1.3 0-3-1.9-3s-2.2 1.4-2.2 2.9V21h-4V9z" />
                  </svg>
                </a>

                <!-- TikTok -->
                <a href="https://www.tiktok.com/@bdbfloor_epoxycat?_r=1&_t=ZS-93K6w7OKGgc" class="social-link" aria-label="TikTok">
                  <svg width="22" height="22" viewBox="0 0 24 24" fill="currentColor">
                    <path
                      d="M16.7 5.3c-1-.6-1.8-1.5-2.2-2.6h-2.6v12.2c0 1.3-1.1 2.4-2.4 2.4S7 16.2 7 14.9c0-1.3 1.1-2.4 2.4-2.4.2 0 .4 0 .6.1V9.9c-.2 0-.4-.1-.6-.1-2.9 0-5.1 2.3-5.1 5.1S6.5 20 9.3 20s5.1-2.3 5.1-5.1V9.1c1.2.8 2.6 1.3 4.1 1.3V7.8c-.6 0-1.2-.2-1.8-.5z"
                    />
                  </svg>
                </a>
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
