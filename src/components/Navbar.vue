<template>
  <MDBNavbar expand="lg" container class="navbar-scroll" :class="{ 'navbar-hidden': !showNavbar }">
    <MDBNavbarBrand>
      <a href="#" class="navbar-brand fw-bold" @click.prevent="scrollToSection('home')">CV. Berkah Doa Bunda</a>
    </MDBNavbarBrand>

    <MDBNavbarToggler @click="collapse = !collapse" />

    <MDBCollapse v-model="collapse">
      <MDBNavbarNav class="d-flex w-100 justify-content-end mb-2 mb-lg-0">
        <MDBNavbarItem>
          <a href="#" class="nav-link" :class="{ active: activeSection === 'home' }" @click.prevent="scrollToSection('home')">Home</a>
        </MDBNavbarItem>

        <MDBNavbarItem>
          <a href="#" class="nav-link" :class="{ active: activeSection === 'about' }" @click.prevent="scrollToSection('about')">Tentang Kami</a>
        </MDBNavbarItem>

        <MDBNavbarItem>
          <MDBDropdown class="nav-item" v-model="dropdown">
            <MDBDropdownToggle tag="a" role="button" class="nav-link" @click.prevent="dropdown = !dropdown" :class="{ active: ['layanan', 'produk', 'policySection', 'warna'].includes(activeSection) }"> Lainnya </MDBDropdownToggle>

            <MDBDropdownMenu>
              <MDBDropdownItem>
                <a href="#" class="dropdown-item" @click.prevent="scrollToSection('layanan')">Layanan</a>
              </MDBDropdownItem>

              <MDBDropdownItem>
                <a href="#" class="dropdown-item" @click.prevent="scrollToSection('produk')">Produk</a>
              </MDBDropdownItem>

              <MDBDropdownItem>
                <a href="#" class="dropdown-item" @click.prevent="scrollToSection('warna')">Katalog Warna</a>
              </MDBDropdownItem>

              <MDBDropdownItem>
                <a href="#" class="dropdown-item" @click.prevent="scrollToSection('kebijakan')">Kebijakan Perusahaan</a>
              </MDBDropdownItem>
            </MDBDropdownMenu>
          </MDBDropdown>
        </MDBNavbarItem>
      </MDBNavbarNav>
    </MDBCollapse>
  </MDBNavbar>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";
import { MDBNavbar, MDBNavbarBrand, MDBNavbarToggler, MDBCollapse, MDBNavbarNav, MDBNavbarItem, MDBDropdown, MDBDropdownToggle, MDBDropdownMenu, MDBDropdownItem } from "mdb-vue-ui-kit";

const collapse = ref(false);
const dropdown = ref(false);
const showNavbar = ref(true);
const activeSection = ref("home");

let lastScroll = 0;
let observer: IntersectionObserver;

const sections = ["home", "about", "layanan", "produk", "warna", "kebijakan"];

// ================= SCROLL TO SECTION =================
const scrollToSection = (id: string) => {
  if (id === "home") {
    window.scrollTo({ top: 0, behavior: "smooth" });
    activeSection.value = "home";
  } else {
    const el = document.getElementById(id);
    if (!el) return;

    const navbar = document.querySelector(".navbar-scroll") as HTMLElement;
    const navbarHeight = navbar?.offsetHeight || 0;
    const top = el.getBoundingClientRect().top + window.scrollY - navbarHeight + 2;

    window.scrollTo({ top, behavior: "smooth" });
  }

  collapse.value = false;
  dropdown.value = false;
};

// ================= HIDE / SHOW NAVBAR =================
const handleScroll = () => {
  const currentScroll = window.scrollY;

  showNavbar.value = currentScroll < lastScroll || currentScroll < 80;
  lastScroll = currentScroll;

  if (currentScroll < 100) {
    activeSection.value = "home";
  }
};

// ================= ACTIVE SECTION TRACKER =================
onMounted(() => {
  window.addEventListener("scroll", handleScroll);

  const navbar = document.querySelector(".navbar-scroll") as HTMLElement;
  const navbarHeight = navbar?.offsetHeight || 0;

  observer = new IntersectionObserver(
    (entries) => {
      const visible = entries.filter((e) => e.isIntersecting);
      if (!visible.length) return;

      const topMost = visible.sort((a, b) => a.boundingClientRect.top - b.boundingClientRect.top)[0];

      activeSection.value = topMost.target.id;
    },
    {
      root: null,
      rootMargin: `-${navbarHeight + 10}px 0px -60% 0px`,
      threshold: 0,
    }
  );

  sections.forEach((id) => {
    const el = document.getElementById(id);
    if (el) observer.observe(el);
  });
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
  if (observer) observer.disconnect();
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
