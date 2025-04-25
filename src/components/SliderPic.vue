<template>
  <!-- Hero Section Begin -->
  <section class="women-banner spad">
    <Carousel
      :autoplay="4000"
      :wrap-around="true"
      :items-to-show="4"
      :mouseDrag="true"
      :transition="500"
    >
      <Slide v-for="product in products" :key="product.id">
        <div class="product-item">
          <div class="pi-pic">
            <img :src="product.image" :alt="product.name" />
            <ul>
              <li class="w-icon active">
                <a href="#"><i class="icon_bag_alt"></i></a>
              </li>
              <li class="quick-view">
                <router-link to="/product">+ Quick View</router-link>
              </li>
              <li v-if="product.hasRandom" class="w-icon">
                <a href="#"><i class="fa fa-random"></i></a>
              </li>
            </ul>
          </div>
          <div class="pi-text">
            <div class="catagory-name">{{ product.category }}</div>
            <a href="#">
              <h5>{{ product.name }}</h5>
            </a>
            <div class="product-price">
              ${{ product.price }}
              <span v-if="product.oldPrice">${{ product.oldPrice }}</span>
            </div>
          </div>
        </div>
      </Slide>
      <template #addons>
        <Navigation />
        <!-- <Pagination /> -->
      </template>
    </Carousel>
  </section>
  <!-- Hero Section End -->
</template>

<script>
import "vue3-carousel/carousel.css";
import { Carousel, Slide, Navigation } from "vue3-carousel";

export default {
  name: "SliderPic",
  components: {
    Carousel,
    Slide,
    Navigation,
    // Pagination,
  },
  data() {
    return {
      products: [
        {
          id: 1,
          name: "Mickey Baggy",
          category: "Coat",
          price: "14.00",
          oldPrice: "35.00",
          image: "img/desk-1.jpg",
          hasRandom: false,
        },
        {
          id: 2,
          name: "Guangzhou sweater",
          category: "Shoes",
          price: "13.00",
          oldPrice: null,
          image: "img/desk-2.jpg",
          hasRandom: false,
        },
        {
          id: 3,
          name: "Pure Pineapple",
          category: "Towel",
          price: "34.00",
          oldPrice: null,
          image: "img/desk-3.jpg",
          hasRandom: false,
        },
        {
          id: 4,
          name: "Converse Shoes",
          category: "Towel",
          price: "34.00",
          oldPrice: null,
          image: "img/desk-4.jpg",
          hasRandom: true,
        },
      ],
    };
  },
};
</script>

<style>
.women-banner {
  width: 100%;
  padding: 20px 0;
  display: block;
  margin-top: 150px;
  margin-bottom: 150px;
}

.product-slider {
  width: 100%;
  display: flex;
  overflow-x: auto;
}

.product-item {
  margin: 0 50px;
  min-width: 200px;
}

.pi-pic img {
  width: 100%;
  height: auto;
}

/* Tambahkan styling dasar untuk memastikan visibilitas */
.carousel__slide {
  padding: 5px;
}
</style>
