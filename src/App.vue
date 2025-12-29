<template>
  <Navbar />
  <Home />
  <Footer />
</template>

<script setup lang="ts">
import Carousel from "./components/Carousel.vue";
import Footer from "./components/Footer.vue";
import Navbar from "./components/Navbar.vue";
import Home from "./views/Home.vue";
</script>

<style>
#app {
  font-family: Roboto, Helvetica, Arial, sans-serif;
}
</style>
