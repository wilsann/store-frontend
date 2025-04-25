<template>
  <div class="partner-logo">
    <div class="container">
      <Carousel
        :autoplay="3000"
        :wrap-around="true"
        :items-to-show="5"
        :mouseDrag="true"
        :transition="500"
      >
        <Slide v-for="(logo, index) in logos" :key="index">
          <div class="logo-item">
            <div class="tablecell-inner">
              <img :src="logo.src" :alt="logo.alt" />
            </div>
          </div>
        </Slide>

        <template #addons>
          <Navigation />
          <Pagination />
        </template>
      </Carousel>
    </div>
  </div>
</template>

<script>
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide, Pagination, Navigation } from "vue3-carousel";

export default {
  name: "PartnerStore",
  components: {
    Carousel,
    Slide,
    Navigation,
    Pagination,
  },
  data() {
    return {
      logos: [
        { src: "img/logo-carousel/logo-1.png", alt: "Partner 1" },
        { src: "img/logo-carousel/logo-2.png", alt: "Partner 2" },
        { src: "img/logo-carousel/logo-3.png", alt: "Partner 3" },
        { src: "img/logo-carousel/logo-4.png", alt: "Partner 4" },
        { src: "img/logo-carousel/logo-5.png", alt: "Partner 5" },
      ],
    };
  },
};
</script>

<style scoped>
.partner-logo {
  padding: 30px 0;
  background-color: #1e1e1e;
}

.logo-item {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 80px;
  margin: 0 10px;
}

.tablecell-inner {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.tablecell-inner img {
  max-height: 40px;
  filter: brightness(0.8);
  opacity: 0.7;
  transition: opacity 0.3s;
}

.tablecell-inner img:hover {
  opacity: 1;
}
</style>
