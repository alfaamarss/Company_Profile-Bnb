<template>
  <MDBNavbar expand="lg" container class="navbar-scroll" :class="{ 'navbar-hidden': !showNavbar }">
    <MDBNavbarBrand>
      <router-link to="/" class="navbar-brand fw-bold"> CV. Berkah Doa Bunda </router-link>
    </MDBNavbarBrand>

    <MDBNavbarToggler @click="collapse = !collapse" />

    <MDBCollapse v-model="collapse">
      <MDBNavbarNav class="d-flex w-100 justify-content-end mb-2 mb-lg-0">
        <!-- HOME -->
        <MDBNavbarItem>
          <router-link to="/" class="nav-link" :class="{ active: route.name === 'home' }"> Home </router-link>
        </MDBNavbarItem>

        <!-- ABOUT -->
        <MDBNavbarItem>
          <router-link to="/about" class="nav-link" :class="{ active: route.name === 'about' }"> Tentang Kami </router-link>
        </MDBNavbarItem>

        <!-- DROPDOWN -->
        <MDBNavbarItem>
          <MDBDropdown class="nav-item" v-model="dropdown">
            <MDBDropdownToggle tag="a" role="button" class="nav-link" href="#" @click.prevent="dropdown = !dropdown" :class="{ active: isHomeSectionActive }"> Lainnya </MDBDropdownToggle>

            <MDBDropdownMenu>
              <MDBDropdownItem>
                <a class="dropdown-item" href="#" @click.prevent="goSection('layanan')">Layanan</a>
              </MDBDropdownItem>
              <MDBDropdownItem>
                <a class="dropdown-item" href="#" @click.prevent="goSection('produk')">Produk</a>
              </MDBDropdownItem>
              <MDBDropdownItem>
                <a class="dropdown-item" href="#" @click.prevent="goSection('warna')">Katalog Warna</a>
              </MDBDropdownItem>
              <MDBDropdownItem>
                <a class="dropdown-item" href="#" @click.prevent="goSection('kebijakan')">Kebijakan</a>
              </MDBDropdownItem>
            </MDBDropdownMenu>
          </MDBDropdown>
        </MDBNavbarItem>
      </MDBNavbarNav>
    </MDBCollapse>
  </MDBNavbar>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from "vue";
import { useRouter, useRoute } from "vue-router";
import { MDBNavbar, MDBNavbarBrand, MDBNavbarToggler, MDBCollapse, MDBNavbarNav, MDBNavbarItem, MDBDropdown, MDBDropdownToggle, MDBDropdownMenu, MDBDropdownItem } from "mdb-vue-ui-kit";

const router = useRouter();
const route = useRoute();

const collapse = ref(false);
const dropdown = ref(false);
const showNavbar = ref(true);
const activeSection = ref<string | null>(null);

let lastScroll = 0;
let observer: IntersectionObserver | null = null;

// ================= SCROLL HANDLER =================
const handleScroll = () => {
  const current = window.scrollY;
  showNavbar.value = current < lastScroll || current < 80;
  lastScroll = current;

  if (current < 80) activeSection.value = null;
};

// ================= ROUTE + SCROLL =================
const goSection = async (id: string) => {
  if (route.name !== "home") {
    await router.push("/");
    await new Promise((r) => setTimeout(r, 120));
  }

  document.getElementById(id)?.scrollIntoView({
    behavior: "smooth",
    block: "start",
  });

  collapse.value = false;
  dropdown.value = false;
};

// ================= ACTIVE DROPDOWN =================
const isHomeSectionActive = computed(() => route.name === "home" && activeSection.value !== null);

// ================= OBSERVER =================
onMounted(() => {
  window.addEventListener("scroll", handleScroll);

  if (!("IntersectionObserver" in window)) return;

  observer = new IntersectionObserver(
    (entries) => {
      const visible = entries.filter((e) => e.isIntersecting);
      if (!visible.length) return;
      activeSection.value = visible[0].target.id;
    },
    {
      rootMargin: "-80px 0px -60% 0px",
    }
  );

  ["layanan", "produk", "warna", "kebijakan"].forEach((id) => {
    const el = document.getElementById(id);
    if (el && observer) observer.observe(el);
  });
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
  observer?.disconnect();
});
</script>

<style scoped>
.navbar-scroll {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 999;
  transition: transform 0.3s ease-in-out, background 0.3s ease;
  background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
  color: white;
}

.navbar-scroll .nav-link,
.navbar-scroll .navbar-brand {
  color: white;
}

.navbar-scroll .nav-link:hover,
.navbar-scroll .nav-link.active {
  color: #ffd700; /* aksen cat/epoxy */
}

/* Hidden saat scroll */
.navbar-hidden {
  transform: translateY(-100%);
}

/* Glass Dropdown */
.dropdown-menu {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border-radius: 12px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  margin-top: 0.5rem;
}

.dropdown-item {
  color: white;
  transition: background 0.3s, color 0.3s;
}

.dropdown-item:hover {
  background: rgba(255, 255, 255, 0.25);
  color: #ffd700;
}
</style>
