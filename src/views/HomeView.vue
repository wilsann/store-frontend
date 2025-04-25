<template>
  <div class="home">
    <HeaderStore />
    <HeroStore />
    <SliderPic />
    <InstaStore />
    <PartnerStore />
    <footer-store/>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderStore from '@/components/HeaderStore.vue';
import HeroStore from '@/components/HeroStore.vue';
import SliderPic from '@/components/SliderPic.vue';
import InstaStore from '@/components/InstaStore.vue';
import PartnerStore from '@/components/PartnerStore.vue';
import FooterStore from '@/components/FooterStore.vue';

export default {
  name: "HomeView",
  components: {
    HeaderStore,
    HeroStore,
    SliderPic,
    InstaStore,
    PartnerStore,
    FooterStore,
  }
};
</script>
