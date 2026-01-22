<template>
  <nav class="navbar navbar-expand-lg custom-navbar" :class="{ 'navbar-hidden': !showNavbar, 'navbar-scrolled': !isTop }">
    <div class="navbar-wrapper">
      <div class="container navbar-inner">
        <!-- BRAND -->
        <router-link to="/" class="navbar-brand d-flex align-items-center gap-2">
          <img src="/logo.png" alt="Logo CV Berkah Doa Bunda" class="brand-logo" />
          <span class="brand-text">CV. Berkah Doa Bunda</span>
        </router-link>

        <!-- TOGGLER -->
        <button class="navbar-toggler" type="button" @click="collapse = !collapse">
          <span class="navbar-toggler-icon"></span>
        </button>

        <!-- MENU -->
        <div class="collapse navbar-collapse d-flex justify-content-center" :class="{ show: collapse }">
          <ul class="navbar-nav gap-lg-3 align-items-lg-center mx-auto">
            <li class="nav-item">
              <router-link to="/" class="nav-link" :class="{ active: route.name === 'home' }" @click="closeAll">Home</router-link>
            </li>

            <li class="nav-item">
              <router-link to="/about" class="nav-link" :class="{ active: route.name === 'about' }" @click="closeAll">Tentang Kami</router-link>
            </li>

            <!-- DROPDOWN -->
            <li class="nav-item dropdown">
              <a href="#" class="nav-link dropdown-toggle" @click.prevent="dropdown = !dropdown">Lainnya</a>
              <ul class="dropdown-menu glass-dropdown" :class="{ show: dropdown }">
                <li><a class="dropdown-item" @click="goSection('layanan')">Layanan</a></li>
                <li><a class="dropdown-item" @click="goSection('produk')">Produk</a></li>
                <li><a class="dropdown-item" @click="goSection('warna')">Katalog Warna</a></li>
                <li><a class="dropdown-item" @click="goSection('kebijakan')">Kebijakan</a></li>
              </ul>
            </li>
          </ul>

          <!-- RIGHT EMAIL -->
          <div class="navbar-contact d-none d-lg-flex">
            <a href="mailto:info@berkahdoabunda.co.id" class="email-link">info@berkahdoabunda.co.id</a>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";
import { useRoute, useRouter } from "vue-router";

const route = useRoute();
const router = useRouter();
const isTop = ref(true);

const collapse = ref(false);
const dropdown = ref(false);
const showNavbar = ref(true);

let lastScroll = 0;

const closeAll = () => {
  collapse.value = false;
  dropdown.value = false;
};

const goSection = async (id: string) => {
  closeAll();
  if (route.name !== "home") {
    await router.push({ name: "home" });
    setTimeout(() => {
      document.getElementById(id)?.scrollIntoView({ behavior: "smooth", block: "start" });
    }, 300);
  } else {
    document.getElementById(id)?.scrollIntoView({ behavior: "smooth", block: "start" });
  }
};

const handleScroll = () => {
  const current = window.scrollY;

  // 👉 DETEKSI PALING ATAS
  isTop.value = current <= 10;

  if (current <= 0) {
    showNavbar.value = true;
    lastScroll = current;
    return;
  }

  if (current > lastScroll && current > 80) {
    showNavbar.value = false;
    closeAll();
  } else {
    showNavbar.value = true;
  }

  lastScroll = current;
};

onMounted(() => window.addEventListener("scroll", handleScroll));
onUnmounted(() => window.removeEventListener("scroll", handleScroll));
</script>

<style scoped>
/* NAVBAR BASE */

.custom-navbar {
  background: transparent !important;
  box-shadow: none !important;
  position: fixed;
  top: 16px; /* jarak dari atas */
  width: 100%;
  z-index: 1000;
  display: flex;
  justify-content: center;
  transition: transform 0.35s ease;
}

.custom-navbar.navbar-scrolled .navbar-wrapper {
  background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
  backdrop-filter: blur(12px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.25);
}

.navbar-wrapper {
  width: calc(100% - 48px); /* tidak full layar */
  max-width: 1280px;
  border-radius: 999px; /* super rounded */

  background: transparent;
  backdrop-filter: none;

  transition:
    background 0.35s ease,
    backdrop-filter 0.35s ease,
    box-shadow 0.35s ease;
}

.navbar-hidden {
  transform: translateY(-100%);
}

/* INNER */
.navbar-inner {
  display: flex;
  align-items: center;
  justify-content: space-between; /* brand kiri, menu tengah, email kanan */
  min-height: 70px;
  width: 100%;
}

/* BRAND */
.brand-text {
  font-weight: 700;
  color: #ffffff;
  font-size: 1.1rem;
}
.brand-logo {
  height: 36px;
  width: auto;
  object-fit: contain;
}

/* MENU */
.navbar-nav {
  display: flex;
  align-items: center;
  margin: 0 auto; /* presisi tengah */
}

.nav-link {
  color: #ffffff;
  font-weight: 500;
  position: relative;
  text-decoration: none;
}

.nav-link.active,
.nav-link:hover {
  color: #fff650f1;
}

/* RIGHT EMAIL */
.navbar-contact {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-left: 32px;

  background: rgba(255, 255, 255, 0.25);
  backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.35);
  box-shadow: 0 8px 25px rgba(13, 110, 253, 0.25);

  color: #ffffff;
  padding: 8px 16px;
  border-radius: 999px;
  font-weight: 600;
}
.navbar-contact a.email-link {
  color: inherit;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.25s ease;
}
.navbar-contact a.email-link:hover {
  color: #fff650f1;
  text-decoration: underline;
}

/* DROPDOWN */
.dropdown-menu {
  background: rgba(255, 255, 255, 0.15);
  border: none;
}
.glass-dropdown {
  background: rgba(255, 255, 255, 0.28);
  backdrop-filter: blur(18px) saturate(160%);
  border-radius: 16px;
  padding: 10px;
  margin-top: 12px;
  border: 1px solid rgba(255, 255, 255, 0.45);
  box-shadow:
    0 20px 40px rgba(0, 0, 0, 0.25),
    inset 0 1px 0 rgba(255, 255, 255, 0.4);
  animation: glassFade 0.25s ease;
}
.glass-dropdown .dropdown-item {
  background: transparent;
  color: #fff;
  font-weight: 600;
  padding: 10px 14px;
  border-radius: 10px;
  transition: all 0.25s ease;
}
.glass-dropdown .dropdown-item:hover {
  background: rgba(255, 255, 255, 0.45);
  color: #fff650f1;
  transform: translateX(4px);
}

@keyframes glassFade {
  from {
    opacity: 0;
    transform: translateY(6px) scale(0.98);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

/* ================= MOBILE FIX ONLY ================= */
@media (max-width: 991px) {
  /* wrapper tetap pill */
  .navbar-wrapper {
    width: calc(100% - 24px);
    border-radius: 24px;
  }

  /* collapse keluar dari pill */
  .navbar-collapse {
    position: absolute;
    top: calc(100% + 12px);
    left: 12px;
    right: 12px;

    margin: 0;
    padding: 20px;

    background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
    backdrop-filter: blur(14px);

    border-radius: 24px;
    box-shadow: 0 25px 45px rgba(0, 0, 0, 0.35);

    opacity: 0;
    transform: translateY(-12px);
    pointer-events: none;

    transition: all 0.3s ease;
    z-index: 999;
  }

  .navbar-collapse.show {
    opacity: 1;
    transform: translateY(0);
    pointer-events: auto;
  }

  /* menu jadi vertikal */
  .navbar-nav {
    flex-direction: column;
    align-items: center;
    gap: 14px;
  }

  .nav-link {
    font-size: 1.1rem;
    font-weight: 600;
  }

  /* dropdown JANGAN absolute di mobile */
  .dropdown-menu {
    position: static;
    float: none;
    transform: none !important;

    margin-top: 10px;
    padding: 12px;

    background: rgba(255, 255, 255, 0.2);
    backdrop-filter: blur(12px);
    border-radius: 16px;
    box-shadow: none;
  }

  .dropdown-menu.show {
    display: block;
  }

  /* sembunyikan email kanan (desktop only) */
  .navbar-contact {
    display: none !important;
  }
}
</style>
