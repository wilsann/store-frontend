<template>
  <div class="related-products spad">
    <div class="container">
      <div class="row">
        <div class="col-lg-12">
          <div class="section-title">
            <h2>Related Products</h2>
          </div>
        </div>
      </div>
      <Carousel
        :autoplay="4000"
        :wrap-around="true"
        :items-to-show="3"
        :mouseDrag="true"
        :transition="500"
      >
        <Slide v-for="product in products" :key="product.id">
          <div class="row">
            <div class="col-lg-3 col-sm-6">
              <div class="product-item">
                <div class="pi-pic">
                  <img :src="product.image" :alt="product.name" />
                  <ul>
                    <li v-if="product.hasRandom" class="w-icon active">
                      <a href="#"><i class="icon_bag_alt"></i></a>
                    </li>
                    <li class="quick-view">
                      <router-link to="/product">+ Quick View</router-link>
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
            </div>

            <!-- <div class="col-lg-3 col-sm-6">
          <div class="product-item">
            <div class="pi-pic">
              <img src="img/products/women-2.jpg" alt="" />
              <ul>
                <li class="w-icon active">
                  <a href="#"><i class="icon_bag_alt"></i></a>
                </li>
                <li class="quick-view"><a href="#">+ Quick View</a></li>
              </ul>
            </div>
            <div class="pi-text">
              <div class="catagory-name">Shoes</div>
              <a href="#">
                <h5>Guangzhou sweater</h5>
              </a>
              <div class="product-price">$13.00</div>
            </div>
          </div>
        </div>
        <div class="col-lg-3 col-sm-6">
          <div class="product-item">
            <div class="pi-pic">
              <img src="img/products/women-3.jpg" alt="" />
              <ul>
                <li class="w-icon active">
                  <a href="#"><i class="icon_bag_alt"></i></a>
                </li>
                <li class="quick-view"><a href="#">+ Quick View</a></li>
              </ul>
            </div>
            <div class="pi-text">
              <div class="catagory-name">Towel</div>
              <a href="#">
                <h5>Pure Pineapple</h5>
              </a>
              <div class="product-price">$34.00</div>
            </div>
          </div>
        </div>
        <div class="col-lg-3 col-sm-6">
          <div class="product-item">
            <div class="pi-pic">
              <img src="img/products/women-4.jpg" alt="" />
              <ul>
                <li class="w-icon active">
                  <a href="#"><i class="icon_bag_alt"></i></a>
                </li>
                <li class="quick-view"><a href="#">+ Quick View</a></li>
              </ul>
            </div>
            <div class="pi-text">
              <div class="catagory-name">Towel</div>
              <a href="#">
                <h5>Converse Shoes</h5>
              </a>
              <div class="product-price">$34.00</div>
            </div>
          </div>
        </div> -->
          </div>
        </Slide>
        <template #addons>
          <Navigation />
          <!-- <Pagination /> -->
        </template>
      </Carousel>
    </div>
  </div>
</template>

<script>
import "vue3-carousel/carousel.css";
import { Carousel, Slide, Navigation } from "vue3-carousel";

export default {
  name: "RelatedProduct",
  components: {
    Carousel,
    Slide,
    Navigation,
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
