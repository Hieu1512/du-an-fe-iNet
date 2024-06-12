<template>
  <div class="w-[72%] m-auto mb-[120px]">
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
    <div class="w-full mb-6 grid grid-cols-3 gap-6">
      <div
        v-for="(course, index) in courses"
        :key="index"
        class="bg-white rounded-lg block overflow-hidden"
      >
        <div class="w-[90%] m-auto">
          <img
            class="h-[250px] m-auto rounded-md mt-[5%] mb-[8%]"
            :src="course.image"
          />
          <span class="text-xl font-bold">{{ course.nameTitle }}</span>
          <p class="mt-3 text-sm mb-8">
            {{ course.description }}
          </p>
          <span class="text-lg">Giảng viên: {{ course.name }}</span>
          <div
            v-if="!course.price"
            class="text-[#6046FF] text-xl font-bold mt-3"
          >
            {{ course.oldPrice }}đ
          </div>
          <div
            v-else-if="course.price !== '0'"
            class="flex items-end mb-4 mt-3"
          >
            <span class="text-sm line-through opacity-50 mb-[1.5px]"
              >{{ course.oldPrice }}đ</span
            >
            <span class="text-[#6046FF] text-xl font-bold ml-2">{{
              course.price + "đ"
            }}</span>
          </div>
          <div v-else class="flex items-end mb-4 mt-3">
            <span class="text-sm line-through opacity-50 mb-[1.5px]"
              >{{ course.oldPrice }}đ</span
            >
            <span class="text-[#6046FF] text-xl font-bold ml-2">Miễn phí</span>
          </div>
          <button
            class="w-full h-12 mb-[5%] rounded-md border border-[#6046FF] text-[#6046FF] text-base font-semibold transition-transform transform-gpu motion-safe:hover:scale-105"
          >
            Đăng ký ngay
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const title = ref("Gói khóa học");
const subTitle = ref("tiêu biểu");

const courses = ref([
  {
    image: "/img/hoctap.jpg",
    nameTitle: "Web Design",
    description:
      "Learn the fundamentals of web design, including HTML, CSS, and responsive design principles. Develop the skills to create visually appealing and user-friendly websites.",
    oldPrice: "500.000",
    price: "199.000",
    name: "Nguyễn Tú Nam",
    buttonText: "Đăng ký ngay",
  },
  {
    image: "/img/hoctap.jpg",
    nameTitle: "Web Design",
    description:
      "Learn the fundamentals of web design, including HTML, CSS, and responsive design principles. Develop the skills to create visually appealing and user-friendly websites.",
    oldPrice: "500.000",
    price: "199.000",
    name: "Nguyễn Tú Nam",
    buttonText: "Đăng ký ngay",
  },
  {
    image: "/img/hoctap.jpg",
    nameTitle: "Web Design",
    description:
      "Learn the fundamentals of web design, including HTML, CSS, and responsive design principles. Develop the skills to create visually appealing and user-friendly websites.",
    oldPrice: "500.000",
    price: "199.000",
    name: "Nguyễn Tú Nam",
    buttonText: "Đăng ký ngay",
  },
]);
</script>
