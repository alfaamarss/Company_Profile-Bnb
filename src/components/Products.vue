<template>
  <section id="produk" class="py-5 bg-light">
    <div class="container">
      <h2 class="mb-4 text-center">Produk Kami</h2>

      <div class="produk-scroll-wrapper">
        <div class="produk-scroll d-flex gap-3">
          <div class="card text-center flex-shrink-0 shadow-sm p-3 produk-card" v-for="(produk, index) in produkList" :key="index" style="width: 180px">
            <img :src="produk.img" alt="" class="img-fluid mb-2 rounded" style="height: 100px; object-fit: cover" />
            <h6 class="fw-bold">{{ produk.title }}</h6>
            <p class="mb-0" style="font-size: 0.85rem">{{ produk.desc }}</p>
          </div>
        </div>
        <!-- Duplicate untuk looping -->
        <div class="produk-scroll d-flex gap-3">
          <div class="card text-center flex-shrink-0 shadow-sm p-3 produk-card" v-for="(produk, index) in produkList" :key="'dup-' + index" style="width: 180px">
            <img :src="produk.img" alt="" class="img-fluid mb-2 rounded" style="height: 100px; object-fit: cover" />
            <h6 class="fw-bold">{{ produk.title }}</h6>
            <p class="mb-0" style="font-size: 0.85rem">{{ produk.desc }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import epoxyImg from "../assets/epoxy.png";
import waterproofingImg from "../assets/waterproofing.png";
import roadMarkingImg from "../assets/road-marking.png";
import protectiveImg from "../assets/protective.png";
import sportFlooringImg from "../assets/sport-flooring.png";
import decorativeImg from "../assets/decorative.png";
import floorHardenerImg from "../assets/floor-hardener.png";
import membranImg from "../assets/membran.png";
import Epoxy1 from "../assets/product/Epoxy1.jpeg";
import Epoxy2 from "../assets/produk/epoxy2.jpg";
import Epoxy3 from "../assets/produk/epoxy3.jpg";

const produkList = [
  { title: "Jasa Pengecatan Lantai Epoxy", desc: "Lantai kuat dan tahan lama", img: Epoxy1 },
  { title: "Jasa Waterproofing", desc: "Lindungi bangunan dari air", img: waterproofingImg },
  { title: "Jasa Road Line Marking", desc: "Tanda batas lantai dan area", img: roadMarkingImg },
  { title: "Jasa Protective Coating", desc: "Perlindungan permukaan logam/non-logam", img: protectiveImg },
  { title: "Jasa Sport Flooring", desc: "Lapangan olahraga berkualitas", img: sportFlooringImg },
  { title: "Jasa Decorative Flooring", desc: "Hiasan lantai dekoratif", img: decorativeImg },
  { title: "Jasa Floor Hardener", desc: "Finishing beton kuat", img: floorHardenerImg },
  { title: "Jasa Membran Bakar Waterproofing", desc: "Lapisan anti bocor", img: membranImg },
];
</script>

<style scoped>
/* Section background */
#produk {
  padding: 2rem 0;
  background: linear-gradient(135deg, #1e3c72, #2a5298, #5dade2);
  color: white;
}

/* Wrapper & scroll */
.produk-scroll-wrapper {
  display: flex;
  overflow-x: auto; /* Scroll manual aktif */
  scroll-behavior: smooth;
  scroll-snap-type: x mandatory;
  gap: 1rem;
  padding-bottom: 1rem;
}

.produk-scroll {
  display: flex;
  gap: 1rem;
}

/* Setiap card sebagai snap point */
.produk-card {
  scroll-snap-align: start;
  min-width: 180px;
  flex-shrink: 0;

  /* Glass effect */
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border-radius: 16px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  transition: transform 0.3s, box-shadow 0.3s, border 0.3s;
  padding: 1rem;
  text-align: center;
  color: white;
}

.produk-card:hover {
  transform: translateY(-5px) scale(1.05);
  box-shadow: 0 12px 25px rgba(0, 0, 0, 0.4);
  border-color: rgba(255, 255, 255, 0.5);
}

.produk-card img {
  border-radius: 12px;
  object-fit: cover;
  height: 100px;
}

/* Text */
.produk-card h6,
.produk-card p {
  color: white;
}

/* Hide scrollbar for Chrome, Safari & Opera */
.produk-scroll-wrapper::-webkit-scrollbar {
  display: none;
}
/* Hide scrollbar for IE, Edge & Firefox */
.produk-scroll-wrapper {
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none; /* Firefox */
}
</style>
