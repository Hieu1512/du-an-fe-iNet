<template>
  <div class="bg-[#F3F3F4] w-full mx-auto">
    <div class="w-[98%] m-auto">
      <button
        class="border-none py-3 text-base w-full mx-auto bg-[#5236ff] text-white rounded-md mt-4 hover:bg-sky-500 flex items-center cursor-pointer"
      >
        <div class="mx-auto">
          Khóa học giao tiếp Ưu đãi sắp kết thúc. Mua ngay
        </div>
        <!-- <i class="fas fa-caret-down"></i> -->
      </button>
      <div class="w-[80%] m-auto flex py-3">
        <div class="flex items-center">
          <div class="ml-5">
            <img
              src="https://static.ladipage.net/5b33575d031f5281797296b9/mschool-20201019033206.png"
              alt="Logo"
              class="w-40 h-20 px-4 py-4"
            />
          </div>
          <div class="ml-5 flex">
            <div class="text-base ml-7">
              <nuxt-link to="/" class="">Trang chủ</nuxt-link>
            </div>
            <div class="text-base ml-7">
              <nuxt-link to="#" class="">Tin tức</nuxt-link>
            </div>
            <div class="text-base ml-7">
              <nuxt-link to="/khoa-hoc" class="">Khóa học</nuxt-link>
            </div>
            <div class="text-base ml-7">
              <nuxt-link to="/khoa-hoc" class="">Kích hoạt khóa học</nuxt-link>
            </div>
            <div class="text-base ml-7">
              <nuxt-link to="/khoa-hoc" class="">Liên hệ</nuxt-link>
            </div>
            <div class="ml-7 text-base mt-1">
              <nuxt-link to="#" class=""
                ><img
                  class="w-5 h-5"
                  src="https://cdn-icons-png.flaticon.com/512/1170/1170627.png"
              /></nuxt-link>
            </div>
          </div>
          <div class="ml-[170px]">
            <nuxt-link to="#" class="text-base mr-7">Đăng nhập</nuxt-link>
            <nuxt-link
              to="#"
              class="bg-[#5236ff] py-3 px-7 border-none rounded-md cursor-pointer text-white hover:bg-sky-500"
              >Đăng ký</nuxt-link
            >
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const response = await useFetch("http://localhost:8000");
console.log(response.data.value);
onMounted(async () => {});
</script>
