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
                <div class="product-thumbs" v-if="productDetails.galleries.length > 0">
                  <Carousel
                    class="product-thumbs-track ps-slider"
                    :autoplay="3000"
                    :wrap-around="true"
                    :items-to-show="5"
                    :mouseDrag="true"
                    :transition="500"
                  >
                    <Slide v-for="thumb in productDetails.galleries" :key="thumb.id">
                      <div
                        class="pt"
                        @click="changeImage(thumb.photo)"
                        :class="thumb.photo == default_pic ? 'active' : ''"
                      >
                        <img :src="thumb.photo" :alt="thumb.alt" />
                      </div>
                    </Slide>
                  </Carousel>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="product-details text-left">
                  <div class="pd-title">
                    <span>{{ productDetails.type }}</span>
                    <h3>{{ productDetails.name }}</h3>
                  </div>
                  <div class="pd-desc">
                    <p v-html="productDetails.description"></p>
                    <h4>${{ productDetails.price }}</h4>
                  </div>
                  <div class="quantity">
                    <router-link to="/cart">
                    <a @click="saveCart(productDetails.id, productDetails.name, productDetails.price, productDetails.galleries[0].photo)" href="#" class="primary-btn pd-cart"
                      >Add To Cart</a
                    ></router-link>
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
import axios from "axios";

export default {
  name: "ProductView",
  components: {
    HeaderStore,
    FooterStore,
    Carousel,
    Slide,
    RelatedProducts,
  },
  data() {
    return {
      default_pic: "",
      productDetails: {
        galleries: []
      },
      userCart: []
    };
  },
  methods: {
    changeImage(urlImage) {
      this.default_pic = urlImage;
    },
    setDataPicture(data) {
      this.productDetails = data;
      this.default_pic = data.galleries[0].photo;
    },
    saveCart(idProduct, nameProduct, priceProduct, photoProduct) {

      var productStored = {
        "id": idProduct,
        "name": nameProduct,
        "price": priceProduct,
        "photo": photoProduct
      }

      this.userCart.push(productStored);
      const parsed = JSON.stringify(this.userCart);
      localStorage.setItem('userCart', parsed);
    }
  },
  mounted() {
    if (localStorage.getItem('userCart')) {
      try {
        this.userCart = JSON.parse(localStorage.getItem('userCart'));
      } catch (error) {
        localStorage.removeItems('userCart');
      }
    }
    axios
      .get("http://127.0.0.1:8000/api/products", {
        params: {
          id: this.$route.params.id,
        },
      })
      .then((res) => (this.setDataPicture(res.data.data)))
      .catch((err) => console.log(err));
  },
};
</script>
