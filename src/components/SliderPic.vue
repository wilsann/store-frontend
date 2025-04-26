<template>
  <!-- Hero Section Begin -->
  <section class="women-banner spad">
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-12 mt-5" v-if="products.length > 0">
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
                  <img :src="product.galleries[0].photo" alt="" />
                  <ul>
                    <li class="w-icon active">
                      <a href="#"><i class="icon_bag_alt"></i></a>
                    </li>
                    <li class="quick-view">
                      <router-link :to="'/product/'+product.id">+ Quick View</router-link>
                    </li>
                  </ul>
                </div>
                <div class="pi-text">
                  <div class="catagory-name">{{ product.type }}</div>
                  <a href="#">
                    <h5>{{ product.name }}</h5>
                  </a>
                  <div class="product-price">
                    ${{ product.price }}
                    <span>$35.00</span>
                  </div>
                </div>
              </div>
            </Slide>
            <template #addons>
              <Navigation />
              <!-- <Pagination /> -->
            </template>
          </Carousel>
        </div>
        <div class="col-lg-12 mt-5" v-else>
          <p>Data tidak ditemukan</p>
        </div>
      </div>
    </div>
  </section>
  <!-- Hero Section End -->
</template>

<script>
import "vue3-carousel/carousel.css";
import { Carousel, Slide, Navigation } from "vue3-carousel";
import axios from "axios";

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
        // {
        //   id: 1,
        //   name: "Mickey Baggy",
        //   category: "Coat",
        //   price: "14.00",
        //   oldPrice: "35.00",
        //   image: "img/desk-1.jpg",
        //   hasRandom: false,
        // }
      ],
    };
  },
  mounted() {
    axios
      .get("http://127.0.0.1:8000/api/products")
      .then((res) => (this.products = res.data.data.data))
      .catch((err) => console.log(err));
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
