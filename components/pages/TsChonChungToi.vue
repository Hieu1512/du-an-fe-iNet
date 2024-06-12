<template>
  <div class="w-[98%] mb-[100px]">
    <div class="text-[45px] flex justify-center mb-8 mt-20">
      <b class="flex items-center">
        <p class="text-blue-600 mr-3">{{ title }}</p>
        {{ subTitle }}
      </b>
    </div>
    <div class="w-full flex">
      <div class="w-[72%] m-auto rounded-xl flex">
        <div class="w-[48%] flex-">
          <div v-for="item in topItems" :key="item.id">
            <nuxt-link :to="item.link">
              <div
                class="bg-[#F9F9F9] h-[200px] mb-8 rounded-3xl flex flex-col"
              >
                <div class="inline-block mt-auto mb-auto">
                  <div class="flex items-center">
                    <img
                      class="w-[100px] h-[130px] rounded-xl mr-4 ml-6"
                      :src="item.imageSrc"
                      :alt="item.alt"
                    />
                    <div class="flex flex-col mr-6 ml-3">
                      <b class="mr-2 text-xl">{{ item.nameTitle }}</b>
                      <p class="text-base text-gray-600 mt-1">
                        {{ item.description }}
                      </p>
                    </div>
                  </div>
                </div>
              </div>
            </nuxt-link>
          </div>
        </div>
        <div class="w-[4%]"></div>
        <div class="w-[48%]">
          <div v-for="item in bottomItems" :key="item.id">
            <nuxt-link :to="item.link">
              <div
                class="bg-[#F9F9F9] h-[200px] mb-8 rounded-3xl flex flex-col"
              >
                <div class="inline-block mt-auto mb-auto">
                  <div class="flex items-center">
                    <img
                      class="w-[100px] h-[130px] rounded-xl mr-4 ml-6"
                      :src="item.imageSrc"
                      :alt="item.alt"
                    />
                    <div class="flex flex-col mr-6 ml-3">
                      <b class="mr-2 text-xl">{{ item.nameTitle }}</b>
                      <p class="text-base text-gray-600 mt-1">
                        {{ item.description }}
                      </p>
                    </div>
                  </div>
                </div>
              </div>
            </nuxt-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const title = ref("Tại sao");
const subTitle = ref("chọn chúng tôi");

const items = ref([
  {
    id: 1,
    nameTitle: "Update mới nhất",
    description:
      "Long established fact that a reader will be distracted by the readable content of a page when looking at its layout",
    imageSrc: "/img/bongden.png",
    alt: "Bóng đèn",
    link: "#",
  },
  {
    id: 2,
    nameTitle: "Bài giảng hấp dẫn",
    description:
      "Long established fact that a reader will be distracted by the readable content of a page when looking at its layout",
    imageSrc: "/img/baigiang.png",
    alt: "Bài giảng",
    link: "#",
  },
  {
    id: 3,
    nameTitle: "Giảng viên chất lượng",
    description:
      "Long established fact that a reader will be distracted by the readable content of a page when looking at its layout",
    imageSrc: "/img/giangvien.png",
    alt: "Giảng viên",
    link: "#",
  },
  {
    id: 4,
    nameTitle: "Nội dung đa dạng",
    description:
      "Long established fact that a reader will be distracted by the readable content of a page when looking at its layout",
    imageSrc: "/img/noidung.png",
    alt: "Nội dung",
    link: "#",
  },
]);

const topItems = ref(items.value.slice(0, 2));
const bottomItems = ref(items.value.slice(2));
</script>
