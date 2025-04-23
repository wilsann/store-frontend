<template>
    <div class="partner-logo">
        <div class="container">
            <Carousel>
                    <div class="logo-carousel">
                        <Slide v-for="slide in 1" :key="slide">
                            <div class="logo-item">
                                <div class="tablecell-inner">
                                    <img src="img/logo-carousel/logo-1.png" alt="" />
                                </div>
                            </div>
                            <!-- <div class="logo-item">
                                <div class="tablecell-inner">
                                    <img src="img/logo-carousel/logo-2.png" alt="" />
                                </div>
                            </div>
                            <div class="logo-item">
                                <div class="tablecell-inner">
                                    <img src="img/logo-carousel/logo-3.png" alt="" />
                                </div>
                            </div>
                            <div class="logo-item">
                                <div class="tablecell-inner">
                                    <img src="img/logo-carousel/logo-4.png" alt="" />
                                </div>
                            </div>
                            <div class="logo-item">
                                <div class="tablecell-inner">
                                    <img src="img/logo-carousel/logo-5.png" alt="" />
                                </div>
                            </div> -->
                        </Slide>
                    </div>
                <template #addons>
                    <Navigation />
                    <Pagination />
                </template>
            </Carousel>
        </div>
    </div>
</template>

<script>
import "vue3-carousel/carousel.css";
import { Carousel, Slide, Pagination, Navigation } from "vue3-carousel";

export default {
    name: 'PartnerStore',
    components: {
        Carousel,
        Slide,
        Navigation,
        Pagination,
    },
}
</script>