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
import tokopedia from "../assets/tokopedia.png";
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

/* FLOATING BUTTON */
.floating-btn {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
  border: none;
  box-shadow: 0 12px 28px rgba(0, 0, 0, 0.45);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.35s ease;
}

.floating-btn:hover {
  transform: scale(1.08);
  box-shadow: 0 16px 35px rgba(0, 0, 0, 0.55);
}

.floating-btn:active {
  transform: scale(0.95);
}

.btn-logo {
  width: 38px;
  height: 38px;
  object-fit: contain;
}

/* CONTACT PANEL */
.contact-panel {
  position: absolute;
  right: 0;
  bottom: 86px;
  width: 240px;
  background: linear-gradient(135deg, #f4f8ff, #e9f0fb);
  border-radius: 18px;
  padding: 14px;
  box-shadow: 0 18px 40px rgba(0, 0, 0, 0.45);
  border: 1px solid rgba(255, 255, 255, 0.35);

  opacity: 0;
  transform: translateY(16px) scale(0.95);
  pointer-events: none;
  transition: all 0.35s cubic-bezier(0.4, 0, 0.2, 1);
}

.contact-panel.open {
  opacity: 1;
  transform: translateY(0) scale(1);
  pointer-events: auto;
}

/* ITEM */
.contact-panel a {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px;
  border-radius: 12px;
  color: #0f2c5c;
  font-weight: 500;
  text-decoration: none;
  transition: all 0.25s ease;
}

.contact-panel a:hover {
  background: rgba(255, 255, 255, 0.55);
  transform: translateX(4px);
}

.contact-panel a:active {
  transform: scale(0.97);
}

/* ICON */
.icon {
  width: 22px;
  height: 22px;
  object-fit: contain;
  filter: drop-shadow(0 2px 3px rgba(0, 0, 0, 0.15));
}

/* RESPONSIVE (MOBILE) */
@media (max-width: 576px) {
  .contact-panel {
    width: 210px;
  }

  .floating-btn {
    width: 58px;
    height: 58px;
  }
}
</style>
