<template>
  <!-- Hero Section Begin -->
  <section class="hero-section">
    <Carousel :items-to-show="1" :autoplay="4000" :transition="500" :wrap-around="true">
      <Slide v-for="(hero, index) in heros" :key="index">
        <div
          class="single-hero-items set-bg"
          :style="{ backgroundImage: `url(${hero.src})` }"
        >
          <div class="container">
            <div class="row banner-info">
              <div class="col-lg-5">
                <span>Bag,kids</span>
                <h1>Black friday</h1>
                <p>
                  Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed
                  do eiusmod tempor incididunt ut labore et dolore
                </p>
                <a href="#" class="primary-btn">Shop Now</a>
              </div>
            </div>
          </div>
        </div>
      </Slide>
      <template #addons>
        <Navigation />
      </template>
    </Carousel>
  </section>
  <!-- Hero Section End -->
</template>

<script>
import "vue3-carousel/carousel.css";
import { Carousel, Slide, Navigation } from "vue3-carousel";

export default {
  name: "HeroStore",
  components: {
    Carousel,
    Slide,
    Navigation,
  },
  data() {
    return {
        heros: [
            { src: "img/hero-1.jpg", alt: "Hero 1" },
            { src: "img/hero-2.jpg", alt: "Hero 2" },
            { src: "img/hero-3.jpg", alt: "Hero 3" },
        ]
    }
  }
};
</script>

<style>
.set-bg {
  width: 100%;
  height: 500px;
}
.banner-info {
  margin-top: 130px;
}
</style>
