<template>
  <div class="product">
    <header-store />
    <!-- Breadcrumb Section Begin -->
    <div class="breacrumb-section text-left">
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
            <div class="breadcrumb-text product-more">
              <router-link to="/"><i class="fa fa-home"></i> Home</router-link>
              <span>Detail</span>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- Breadcrumb Section Begin -->

    <!-- Product Shop Section Begin -->
    <section class="product-shop spad page-details">
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
            <div class="row">
              <div class="col-lg-6">
                <div class="product-pic-zoom">
                  <img class="product-big-img" :src="default_pic" alt="" />
                </div>
                <div class="product-thumbs">
                  <Carousel
                    class="product-thumbs-track ps-slider"
                    :autoplay="3000"
                    :wrap-around="true"
                    :items-to-show="5"
                    :mouseDrag="true"
                    :transition="500"
                  >
                  <Slide v-for="(picture, index) in pictures" :key="index">
                    <div class="pt" :class="{ active: picture.src === default_pic }" @click="changeImage(picture.src)">
                      <img :src="picture.src" :alt="picture.alt" />
                    </div>
                  </Slide>

                    <!-- <div class="pt" data-imgbigurl="img/mickey2.jpg">
                      <img src="img/mickey2.jpg" alt="" />
                    </div>

                    <div class="pt" data-imgbigurl="img/mickey3.jpg">
                      <img src="img/mickey3.jpg" alt="" />
                    </div>

                    <div class="pt" data-imgbigurl="img/mickey4.jpg">
                      <img src="img/mickey4.jpg" alt="" />
                    </div> -->
                  </Carousel>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="product-details text-left">
                  <div class="pd-title">
                    <span>oranges</span>
                    <h3>Pure Pineapple</h3>
                  </div>
                  <div class="pd-desc">
                    <p>
                      Lorem ipsum dolor sit amet consectetur adipisicing elit.
                      Corporis, error officia. Rem aperiam laborum voluptatum
                      vel, pariatur modi hic provident eum iure natus quos non a
                      sequi, id accusantium! Autem.
                    </p>
                    <p>
                      Lorem ipsum dolor sit, amet consectetur adipisicing elit.
                      Quam possimus quisquam animi, commodi, nihil voluptate
                      nostrum neque architecto illo officiis doloremque et
                      corrupti cupiditate voluptatibus error illum. Commodi
                      expedita animi nulla aspernatur. Id asperiores blanditiis,
                      omnis repudiandae iste inventore cum, quam sint molestiae
                      accusamus voluptates ex tempora illum sit perspiciatis.
                      Nostrum dolor tenetur amet, illo natus magni veniam quia
                      sit nihil dolores. Commodi ratione distinctio harum
                      voluptatum velit facilis voluptas animi non laudantium, id
                      dolorem atque perferendis enim ducimus? A exercitationem
                      recusandae aliquam quod. Itaque inventore obcaecati, unde
                      quam impedit praesentium veritatis quis beatae ea atque
                      perferendis voluptates velit architecto?
                    </p>
                    <h4>$495.00</h4>
                  </div>
                  <div class="quantity">
                    <router-link to="/cart" class="primary-btn pd-cart"
                      >Add To Cart</router-link
                    >
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- Product Shop Section End -->
    <related-products />
    <footer-store />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderStore from "@/components/HeaderStore.vue";
import FooterStore from "@/components/FooterStore.vue";
import RelatedProducts from "@/components/RelatedProducts.vue";
import { Carousel, Slide } from "vue3-carousel";

export default {
  name: "ProductView",
  components: {
    HeaderStore,
    FooterStore,
    Carousel,
    Slide,
    RelatedProducts
  },
  data() {
    return {
        default_pic: "img/mickey1.jpg",
        pictures: [
            { src: "img/mickey1.jpg", alt: "Mickey-1" },
            { src: "img/mickey2.jpg", alt: "Mickey-2" },
            { src: "img/mickey3.jpg", alt: "Mickey-3" },
            { src: "img/mickey4.jpg", alt: "Mickey-4" }
        ]
    }
  },
  methods: {
    changeImage(urlImage) {
        this.default_pic = urlImage;
    }
  }
};
</script>
