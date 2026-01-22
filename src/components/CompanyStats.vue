<template>
  <section class="stats-section text-white">
    <div class="container">
      <div class="row g-4 text-center">
        <div class="col-6 col-md-3" v-for="stat in stats" :key="stat.label">
          <div class="stat-card">
            <div class="stat-icon" v-html="stat.icon" />
            <h2 class="stat-value">{{ stat.value }}</h2>
            <p class="stat-label">{{ stat.label }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const stats = [
  {
    value: "10+",
    label: "Tahun Pengalaman",
    icon: `
     <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24"><path fill="#fbd000" d="m5.825 21l1.625-7.025L2 9.25l7.2-.625L12 2l2.8 6.625l7.2.625l-5.45 4.725L18.175 21L12 17.275z"/></svg>
    `,
  },
  {
    value: "150+",
    label: "Proyek Selesai",
    icon: `
      <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24"><path fill="#fbd000" d="M4 21V9l8-6l8 6v12h-6v-7h-4v7z"/></svg>
    `,
  },
  {
    value: "98%",
    label: "Klien Puas",
    icon: `
    <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24"><g fill="none" fill-rule="evenodd"><path d="m12.594 23.258l-.012.002l-.071.035l-.02.004l-.014-.004l-.071-.036q-.016-.004-.024.006l-.004.01l-.017.428l.005.02l.01.013l.104.074l.015.004l.012-.004l.104-.074l.012-.016l.004-.017l-.017-.427q-.004-.016-.016-.018m.264-.113l-.014.002l-.184.093l-.01.01l-.003.011l.018.43l.005.012l.008.008l.201.092q.019.005.029-.008l.004-.014l-.034-.614q-.005-.019-.02-.022m-.715.002a.02.02 0 0 0-.027.006l-.006.014l-.034.614q.001.018.017.024l.015-.002l.201-.093l.01-.008l.003-.011l.018-.43l-.003-.012l-.01-.01z"/><path fill="#fbd000" d="M12 2c5.523 0 10 4.477 10 10s-4.477 10-10 10S2 17.523 2 12S6.477 2 12 2m1.984 12.25c-.53.468-1.223.75-1.984.75a3 3 0 0 1-1.984-.75a1 1 0 1 0-1.324 1.5A5 5 0 0 0 12 17a4.98 4.98 0 0 0 3.308-1.25a1 1 0 0 0-1.324-1.5M8.5 8c-1.087 0-1.958.68-2.394 1.552a1 1 0 0 0 1.73.997l.058-.101c.162-.324.41-.448.606-.448c.17 0 .382.095.541.336l.065.112a1 1 0 0 0 1.788-.896C10.457 8.68 9.587 8 8.5 8m7 0c-1.087 0-1.957.68-2.394 1.552a1 1 0 0 0 1.73.997l.058-.101c.162-.324.41-.448.606-.448c.17 0 .382.095.541.336l.065.112a1 1 0 1 0 1.788-.896C17.458 8.68 16.587 8 15.5 8"/></g></svg>
    `,
  },
  {
    value: "20+",
    label: "Tenaga Profesional",
    icon: `
   <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24"><g fill="none" fill-rule="evenodd"><path d="m12.594 23.258l-.012.002l-.071.035l-.02.004l-.014-.004l-.071-.036q-.016-.004-.024.006l-.004.01l-.017.428l.005.02l.01.013l.104.074l.015.004l.012-.004l.104-.074l.012-.016l.004-.017l-.017-.427q-.004-.016-.016-.018m.264-.113l-.014.002l-.184.093l-.01.01l-.003.011l.018.43l.005.012l.008.008l.201.092q.019.005.029-.008l.004-.014l-.034-.614q-.005-.019-.02-.022m-.715.002a.02.02 0 0 0-.027.006l-.006.014l-.034.614q.001.018.017.024l.015-.002l.201-.093l.01-.008l.003-.011l.018-.43l-.003-.012l-.01-.01z"/><path fill="#fbd000" d="M12 2c5.523 0 10 4.477 10 10s-4.477 10-10 10S2 17.523 2 12S6.477 2 12 2m1.984 12.25c-.53.468-1.223.75-1.984.75a3 3 0 0 1-1.984-.75a1 1 0 1 0-1.324 1.5A5 5 0 0 0 12 17a4.98 4.98 0 0 0 3.308-1.25a1 1 0 0 0-1.324-1.5M8.5 8c-1.087 0-1.958.68-2.394 1.552a1 1 0 0 0 1.73.997l.058-.101c.162-.324.41-.448.606-.448c.17 0 .382.095.541.336l.065.112a1 1 0 0 0 1.788-.896C10.457 8.68 9.587 8 8.5 8m7 0c-1.087 0-1.957.68-2.394 1.552a1 1 0 0 0 1.73.997l.058-.101c.162-.324.41-.448.606-.448c.17 0 .382.095.541.336l.065.112a1 1 0 1 0 1.788-.896C17.458 8.68 16.587 8 15.5 8"/></g></svg>
    `,
  },
];
</script>

<style scoped>
/* SECTION */
.stats-section {
  background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
  padding: 4rem 0;
}

/* CARD */
.stat-card {
  height: 100%;
  padding: 30px 18px;
  border-radius: 22px;

  background: rgba(255, 255, 255, 0.18);
  backdrop-filter: blur(14px);

  border: 1px solid rgba(255, 255, 255, 0.3);
  box-shadow:
    0 12px 30px rgba(0, 0, 0, 0.35),
    inset 0 1px 0 rgba(255, 255, 255, 0.35);

  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
}

/* ICON */
.stat-icon {
  width: 56px;
  height: 56px;
  margin: 0 auto 12px;

  display: flex;
  align-items: center;
  justify-content: center;

  border-radius: 50%;
  background: rgba(255, 255, 255, 0.25);
  backdrop-filter: blur(10px);

  color: #fff650f1;
}

.stat-icon svg {
  width: 28px;
  height: 28px;
}

/* HOVER */
@media (hover: hover) {
  .stat-card:hover {
    transform: translateY(-8px);
    box-shadow:
      0 20px 45px rgba(0, 0, 0, 0.45),
      inset 0 1px 0 rgba(255, 255, 255, 0.45);
  }
}

/* VALUE */
.stat-value {
  font-size: 2.3rem;
  font-weight: 800;
  letter-spacing: 1px;
  margin-bottom: 6px;
  color: #fff650f1;
}

/* LABEL */
.stat-label {
  font-size: 0.95rem;
  font-weight: 600;
  opacity: 0.9;
}

/* MOBILE */
@media (max-width: 575px) {
  .stat-value {
    font-size: 2rem;
  }
}
</style>
