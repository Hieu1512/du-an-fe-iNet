<template>
  <div class="w-[72%] m-auto mb-[100px]">
    <div class="flex items-center justify-between mb-8">
      <h2 class="text-[40px] flex font-semibold">
        {{ title }}
        <p class="ml-3 text-[#6046FF]">{{ subTitle }}</p>
      </h2>
      <button
        class="bg-white text-black rounded-md px-5 py-3 text-center block ml-auto"
      >
        Xem thêm
      </button>
    </div>
    <div class="w-full h-auto mb-6 grid grid-cols-4 gap-6">
      <div
        v-for="(course, index) in courses"
        :key="index"
        class="bg-white rounded-lg block overflow-hidden transition-transform duration-300 transform-gpu motion-safe:hover:scale-110"
      >
        <img class="rounded-none w-full h-[130px]" :src="course.image" />
        <div class="w-[86%] m-auto mt-4">
          <div class="flex items-center mb-3">
            <img class="w-4 h-4" src="/img/chayphat.png" />
            <p class="ml-2 text-xs">{{ course.lessons }} bài giảng</p>
          </div>
          <h1 class="text-[17px] font-semibold mb-3">{{ course.title }}</h1>
          <div v-if="!course.price" class="text-[#6046FF] text-xl font-bold">
            {{ course.oldPrice }}đ
          </div>
          <div v-else-if="course.price !== '0'" class="flex items-end mb-4">
            <span class="text-sm line-through opacity-50 mb-[1.5px]"
              >{{ course.oldPrice }}đ</span
            >
            <span class="text-[#6046FF] text-xl font-bold ml-2">{{
              course.price + "đ"
            }}</span>
          </div>
          <div v-else class="flex items-end mb-4">
            <span class="text-sm line-through opacity-50 mb-[1.5px]"
              >{{ course.oldPrice }}đ</span
            >
            <span class="text-[#6046FF] text-xl font-bold ml-2">Miễn phí</span>
          </div>
          <hr />
          <div class="flex mt-4 mb-4">
            <img class="rounded-full w-5 h-5" :src="course.authorImage" />
            <span class="text-sm ml-2">{{ course.author }}</span>
            <button
              class="bg-[#6046FF] text-white ml-3 text-sm rounded-md font-thin px-2 py-0.5 text-center block hover:bg-sky-500"
            >
              {{ course.buttonText }}
            </button>
          </div>
        </div>
        <div class="w-[2.4%]"></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const title = ref("Khóa học");
const subTitle = ref("nổi bật");

const courses = ref([
  {
    image:
      "https://cdn.tgdd.vn/Products/Images/44/313619/Slider/vi-vn-lenovo-yoga-7-14irl8-i7-82yl006bvn-slider-6.jpg",
    lessons: 20,
    title: "Lập trình hướng đối tượng",
    oldPrice: "500.000",
    price: "199.000",
    authorImage:
      "https://img.lovepik.com/free-png/20211107/lovepik-confident-workplace-business-male-image-png-image_400441790_wh1200.png",
    author: "Nguyễn Tú Nam",
    buttonText: "Mua ngay",
  },
  {
    image:
      "https://cdn.tgdd.vn/Products/Images/44/313619/Slider/vi-vn-lenovo-yoga-7-14irl8-i7-82yl006bvn-slider-6.jpg",
    lessons: 20,
    title: "Lập trình hướng đối tượng",
    oldPrice: "500.000",
    price: "0",
    authorImage:
      "https://img.lovepik.com/free-png/20211107/lovepik-confident-workplace-business-male-image-png-image_400441790_wh1200.png",
    author: "Nguyễn Tú Nam",
    buttonText: "Xem ngay",
  },
  {
    image:
      "https://cdn.tgdd.vn/Products/Images/44/313619/Slider/vi-vn-lenovo-yoga-7-14irl8-i7-82yl006bvn-slider-6.jpg",
    lessons: 20,
    title: "Lập trình hướng đối tượng",
    oldPrice: "500.000",
    price: "199.000",
    authorImage:
      "https://img.lovepik.com/free-png/20211107/lovepik-confident-workplace-business-male-image-png-image_400441790_wh1200.png",
    author: "Nguyễn Tú Nam",
    buttonText: "Mua ngay",
  },
  {
    image:
      "https://cdn.tgdd.vn/Products/Images/44/313619/Slider/vi-vn-lenovo-yoga-7-14irl8-i7-82yl006bvn-slider-6.jpg",
    lessons: 20,
    title: "Lập trình hướng đối tượng",
    oldPrice: "500.000",
    price: "0",
    authorImage:
      "https://img.lovepik.com/free-png/20211107/lovepik-confident-workplace-business-male-image-png-image_400441790_wh1200.png",
    author: "Nguyễn Tú Nam",
    buttonText: "Xem ngay",
  },
  {
    image:
      "https://cdn.tgdd.vn/Products/Images/44/313619/Slider/vi-vn-lenovo-yoga-7-14irl8-i7-82yl006bvn-slider-6.jpg",
    lessons: 20,
    title: "Lập trình hướng đối tượng",
    oldPrice: "500.000",
    price: "199.000",
    authorImage:
      "https://img.lovepik.com/free-png/20211107/lovepik-confident-workplace-business-male-image-png-image_400441790_wh1200.png",
    author: "Nguyễn Tú Nam",
    buttonText: "Mua ngay",
  },
  {
    image:
      "https://cdn.tgdd.vn/Products/Images/44/313619/Slider/vi-vn-lenovo-yoga-7-14irl8-i7-82yl006bvn-slider-6.jpg",
    lessons: 20,
    title: "Lập trình hướng đối tượng",
    oldPrice: "500.000",
    price: "0",
    authorImage:
      "https://img.lovepik.com/free-png/20211107/lovepik-confident-workplace-business-male-image-png-image_400441790_wh1200.png",
    author: "Nguyễn Tú Nam",
    buttonText: "Xem ngay",
  },
  {
    image:
      "https://cdn.tgdd.vn/Products/Images/44/313619/Slider/vi-vn-lenovo-yoga-7-14irl8-i7-82yl006bvn-slider-6.jpg",
    lessons: 20,
    title: "Lập trình hướng đối tượng",
    oldPrice: "500.000",
    price: "199.000",
    authorImage:
      "https://img.lovepik.com/free-png/20211107/lovepik-confident-workplace-business-male-image-png-image_400441790_wh1200.png",
    author: "Nguyễn Tú Nam",
    buttonText: "Mua ngay",
  },
  {
    image:
      "https://cdn.tgdd.vn/Products/Images/44/313619/Slider/vi-vn-lenovo-yoga-7-14irl8-i7-82yl006bvn-slider-6.jpg",
    lessons: 20,
    title: "Lập trình hướng đối tượng",
    oldPrice: "500.000",
    price: "0",
    authorImage:
      "https://img.lovepik.com/free-png/20211107/lovepik-confident-workplace-business-male-image-png-image_400441790_wh1200.png",
    author: "Nguyễn Tú Nam",
    buttonText: "Xem ngay",
  },
]);

function displayOriginalPrice(course) {
  if (course.price === "Miễn phí") {
    return "500 000";
  } else if (course.oldPrice) {
    return course.oldPrice;
  } else {
    return "";
  }
}

function displayPrice(course) {
  if (course.price === "Miễn phí") {
    return "Miễn phí";
  } else {
    return course.price;
  }
}
</script>
