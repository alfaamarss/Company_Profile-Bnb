<template>
  <MDBNavbar expand="lg" bg="body-tertiary" container class="navbar-scroll" :class="{ 'navbar-hidden': !showNavbar }">
    <MDBNavbarBrand>
      <a href="#" class="navbar-brand fw-bold">Cv. Berkah Doa Bunda</a>
    </MDBNavbarBrand>

    <MDBNavbarToggler @click="collapse = !collapse" />
    <MDBCollapse v-model="collapse">
      <MDBNavbarNav class="d-flex w-100 justify-content-end mb-2 mb-lg-0">
        <MDBNavbarItem><a href="#" class="nav-link active">Home</a></MDBNavbarItem>
        <MDBNavbarItem><a href="#" class="nav-link">Link</a></MDBNavbarItem>
        <MDBNavbarItem>
          <MDBDropdown class="nav-item" v-model="dropdown">
            <MDBDropdownToggle tag="a" class="nav-link" @click="dropdown = !dropdown"> Dropdown </MDBDropdownToggle>
            <MDBDropdownMenu>
              <MDBDropdownItem><a href="#" class="dropdown-item">Action</a></MDBDropdownItem>
              <MDBDropdownItem><a href="#" class="dropdown-item">Another Action</a></MDBDropdownItem>
              <MDBDropdownItem><a href="#" class="dropdown-item">Something else here</a></MDBDropdownItem>
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
let lastScroll = 0;

const handleScroll = () => {
  const currentScroll = window.pageYOffset || document.documentElement.scrollTop;
  showNavbar.value = currentScroll < lastScroll || currentScroll < 100;
  lastScroll = currentScroll;
};

onMounted(() => window.addEventListener("scroll", handleScroll));
onUnmounted(() => window.removeEventListener("scroll", handleScroll));
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
