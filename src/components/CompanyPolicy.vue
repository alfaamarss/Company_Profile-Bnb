<template>
  <section id="kebijakan" class="py-5 kebijakan">
    <div class="container">
      <h2 class="mb-5 text-center reveal-title">Kebijakan Perusahaan</h2>

      <div class="row g-4 reveal" ref="policySection">
        <!-- MUTU -->
        <div class="col-lg-6 fade-left">
          <div class="card shadow-sm h-100">
            <div class="card-body">
              <h5 class="card-title fw-bold mb-3">🏅 Kebijakan Mutu</h5>
              <p>
                CV. <strong>Berkah Doa Bunda</strong> melaksanakan setiap pekerjaan secara konsisten dan konsekuen melalui perbaikan berkelanjutan di seluruh aspek operasional guna meningkatkan kualitas pelayanan dan menghasilkan produk
                berkualitas demi kepuasan pelanggan.
              </p>
            </div>
          </div>
        </div>

        <!-- K3 -->
        <div class="col-lg-6 fade-right">
          <div class="card shadow-sm h-100">
            <div class="card-body">
              <h5 class="card-title fw-bold mb-3">🦺 Kebijakan K3</h5>
              <p>
                CV. <strong>Berkah Doa Bunda</strong> berkomitmen menjamin keselamatan dan kesehatan kerja bagi seluruh karyawan dan pihak terkait di kantor maupun lokasi proyek dengan mematuhi peraturan K3 serta menciptakan lingkungan
                kerja yang aman, sehat, dan produktif.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { onMounted, ref } from "vue";
const policySection = ref<HTMLElement | null>(null);

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        entry.target.classList.toggle("active", entry.isIntersecting);
      });
    },
    { threshold: 0.3 },
  );

  if (policySection.value) observer.observe(policySection.value);
});
</script>

<style scoped>
.kebijakan {
  background: linear-gradient(135deg, #5dade2, #1e3c72, #2a5298);
  color: white;
}

.card {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border-radius: 16px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  color: white;
}

.card-title,
.card-body p {
  color: white;
}
</style>
