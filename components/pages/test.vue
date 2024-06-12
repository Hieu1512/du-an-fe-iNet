<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, Pagination } from "swiper/modules";
import "swiper/css";

const modules = [Autoplay, Pagination];
const mySwiper = ref();
</script>

<template>
  <div class="container">
    <Swiper
      :modules="modules"
      @swiper="(s) => (mySwiper = s)"
      :slides-per-view="1"
      :breakpoints="{
        300: {
          slidesPerView: 1.175,
        },
        400: {
          slidesPerView: 1.515,
        },
        768: {
          slidesPerView: 3,
          spaceBetween: 20,
        },
        1024: {
          slidesPerView: 4,
        },
      }"
      :space-between="30"
      loop
      :autoplay="{
        delay: 3000,
        disableOnInteraction: false,
        pauseOnMouseEnter: true,
      }"
      :speed="1000"
      class="!z-0 rounded-lg"
    >
      <SwiperSlide v-for="(item, index) of 8" :key="index">
        <div class="bg-red-500 w-full">Test {{ index }}</div>
      </SwiperSlide>
    </Swiper>
  </div>
</template>
