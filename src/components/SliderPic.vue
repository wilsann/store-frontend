<template>
  <!-- Hero Section Begin -->
  <section class="women-banner spad">
    <Carousel>
      <Slide v-for="slide in 3" :key="slide">
        <div class="container-fluid">
          <div class="row">
            <div class="col-lg-12 mt-5">
              <div class="product-slider">
                <div class="product-item">
                  <div class="pi-pic">
                    <img src="img/mickey1.jpg" alt="" />
                    <ul>
                      <li class="w-icon active">
                        <a href="#"><i class="icon_bag_alt"></i></a>
                      </li>
                      <li class="quick-view">
                        <a href="product.html">+ Quick View</a>
                      </li>
                    </ul>
                  </div>
                  <div class="pi-text">
                    <div class="catagory-name">Coat</div>
                    <a href="#">
                      <h5>Mickey Baggy</h5>
                    </a>
                    <div class="product-price">
                      $14.00
                      <span>$35.00</span>
                    </div>
                  </div>
                </div>
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
                <div class="product-item">
                  <div class="pi-pic">
                    <img src="img/products/women-4.jpg" alt="" />
                    <ul>
                      <li class="w-icon active">
                        <a href="#"><i class="icon_bag_alt"></i></a>
                      </li>
                      <li class="quick-view"><a href="#">+ Quick View</a></li>
                      <li class="w-icon">
                        <a href="#"><i class="fa fa-random"></i></a>
                      </li>
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
              </div>
            </div>
          </div>
        </div>
      </Slide>
      <template #addons>
        <Navigation />
        <Pagination />
      </template>
    </Carousel>
  </section>
  <!-- Hero Section End -->
</template>

<script>
import "vue3-carousel/carousel.css";
import { Carousel, Slide, Pagination, Navigation } from "vue3-carousel";

// const config = {
//   height: 200,
//   itemsToShow: 2,
//   gap: 5,
//   autoplay: 4000,
//   wrapAround: true,
//   pauseAutoplayOnHover: true,
// }

export default {
  name: "SliderPic",
  components: {
    Carousel,
    Slide,
    Navigation,
    Pagination,
  },
};
</script>

<style>
.women-banner {
  width: 100%;
  padding: 20px 0;
  display: block;
}

.product-slider {
  width: 100%;
  display: flex;
  overflow-x: auto;
}

.product-item {
  margin: 0 10px;
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
