<template>
  <section id="kontak" class="py-5" style="background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2)">
    <div class="container">
      <h2 class="mb-5 text-center text-white">Kontak Kami</h2>

      <!-- Card Glass -->
      <div class="glass-card mx-auto p-4 shadow-lg">
        <div class="row align-items-center g-4">
          <!-- Kontak -->
          <div class="col-md-6">
            <ul class="list-group list-group-flush">
              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span class="d-flex align-items-center gap-2">
                  <!-- Phone SVG -->
                  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="white" viewBox="0 0 16 16">
                    <path
                      d="M3.654 1.328a.678.678 0 0 1 .76-.057l2.27 1.135c.329.164.445.558.27.857L6.133 5.93a.678.678 0 0 1-.738.26l-1.282-.321a11.745 11.745 0 0 0 5.516 5.516l.321-1.282a.678.678 0 0 1 .26-.738l1.267-1.027a.678.678 0 0 1 .857.27l1.135 2.27a.678.678 0 0 1-.057.76l-1.516 1.516a1.745 1.745 0 0 1-1.987.378c-2.637-1.036-4.992-3.39-6.028-6.028a1.745 1.745 0 0 1 .378-1.987L3.654 1.328z"
                    />
                  </svg>
                  Telepon
                </span>
                <a href="tel:085212714789" class="text-decoration-none text-white">0852-1271-4789</a>
              </li>

              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span class="d-flex align-items-center gap-2">
                  <!-- Email SVG -->
                  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="white" viewBox="0 0 16 16">
                    <path d="M0 4a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v0.217l-8 4.8-8-4.8V4zm0 1.383V12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V5.383l-7.555 4.533a.5.5 0 0 1-.49 0L0 5.383z" />
                  </svg>
                  Email
                </span>
                <a href="mailto:cv.berkahdoabunda@gmail.com" class="text-decoration-none text-white">cv.berkahdoabunda@gmail.com</a>
              </li>

              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span><img :src="wa" class="icon" /> Chat WA</span>
                <a href="https://wa.me/6285212714789" target="_blank" class="btn btn-success btn-sm">Hubungi via WhatsApp</a>
              </li>
              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span><img :src="tokopedia" class="icon" /> Tokopedia</span>
                <a href="https://www.tokopedia.com/nama-toko" target="_blank" class="btn btn-warning btn-sm">Kunjungi Toko</a>
              </li>
              <li class="list-group-item d-flex justify-content-between align-items-center">
                <span><img :src="shopee" class="icon" /> Shopee</span>
                <a href="https://shopee.co.id/nama-toko" target="_blank" class="btn btn-danger btn-sm">Kunjungi Toko</a>
              </li>
            </ul>
          </div>

          <!-- Logo -->
          <div class="col-md-6 text-center">
            <img :src="logo" alt="Logo CV Berkah Doa Bunda" class="img-fluid rounded" style="max-height: 250px" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import logo from "../assets/logo.png";

import wa from "../assets/wa.png";
import tokopedia from "../assets/tokopedia.jpeg";
import shopee from "../assets/shopee.png";
</script>

<style scoped>
h2 {
  font-weight: 600;
}

.glass-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(15px);
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  color: white;
  padding: 1rem;
  transition: transform 0.3s, box-shadow 0.3s;
}

.glass-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 25px rgba(0, 0, 0, 0.4);
}

.list-group-item {
  border: none;
  background: transparent;
}

.list-group-item span,
.list-group-item a {
  color: white;
  display: flex;
  align-items: center;
  gap: 8px;
}

.icon {
  width: 24px;
  height: 24px;
  object-fit: contain;
}

.btn-sm {
  font-size: 0.8rem;
}

.glass-card img {
  max-height: 250px;
  border-radius: 20px;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.5);
}
</style>
