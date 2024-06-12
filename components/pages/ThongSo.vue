<template>
  <div class="w-[72%] h-[250px] bg-[#F9F9F9] m-auto rounded-xl mb-12 flex">
    <div
      v-for="item in items"
      :key="item.id"
      class="w-1/3 h-[250px] flex items-center justify-center"
    >
      <div class="text-center animate-fade-in">
        <span class="text-6xl flex font-bold mb-3"
          >{{ item.value }}
          <p class="text-[blue] font-bold">+</p></span
        >
        <span class="text-xl">{{ item.label }}</span>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";

const items = ref([
  { id: 1, value: 300, label: "Giảng viên" },
  { id: 2, value: 20000, label: "Học viên" },
  { id: 3, value: 10000, label: "Bài giảng" },
]);
</script>
