<template>
  <div class="floating-wrapper">
    <div class="contact-panel" :class="{ open }">
      <a href="tel:085212714789">
        <span>📞 </span>
        <span>0852-1271-4789</span>
      </a>

      <a href="https://wa.me/6285212714789" target="_blank">
        <img :src="wa" class="icon" />
        <span> WhatsApp</span>
      </a>

      <a href="https://www.tokopedia.com/nama-toko" target="_blank">
        <img :src="tokopedia" class="icon" />
        <span>Tokopedia</span>
      </a>

      <a href="https://shopee.co.id/nama-toko" target="_blank">
        <img :src="shopee" class="icon" />
        <span>Shopee</span>
      </a>
    </div>

    <button class="floating-btn" @click="open = !open">
      <img :src="logo" class="btn-logo" />
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import logo from "../assets/logo.png";
import wa from "../assets/wa.png";
import tokopedia from "../assets/tokopedia.jpeg";
import shopee from "../assets/shopee.png";

const open = ref(false);
</script>

<style scoped>
.floating-wrapper {
  position: fixed;
  right: 24px;
  bottom: 24px;
  z-index: 1000;
}

.floating-btn {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
  border: none;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.btn-logo {
  width: 38px;
  height: 38px;
  object-fit: contain;
}

.contact-panel {
  position: absolute;
  right: 0;
  bottom: 80px;
  width: 230px;
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(15px);
  border-radius: 18px;
  padding: 12px;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.45);
  border: 1px solid rgba(255, 255, 255, 0.25);
  opacity: 0;
  transform: translateY(10px);
  pointer-events: none;
  transition: 0.3s ease;
}

.contact-panel.open {
  opacity: 1;
  transform: translateY(0);
  pointer-events: auto;
}

.contact-panel a {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px;
  border-radius: 10px;
  color: white;
  font-weight: 500;
  text-decoration: none;
}

.contact-panel a:hover {
  background: rgba(255, 255, 255, 0.2);
}

.contact-panel small {
  display: block;
  font-size: 0.7rem;
  opacity: 0.8;
}

.icon {
  width: 22px;
  height: 22px;
  object-fit: contain;
}
</style>
