<template>
  <div class="w-[72%] m-auto">
    <div class="flex items-center justify-between mb-8">
      <h2 class="text-[40px] flex font-semibold">
        Đối tác
        <p class="ml-3 text-[#6046FF]">tiêu biểu</p>
      </h2>
    </div>
    <div class="flex justify-center">
      <div
        v-for="(partner, index) in partners"
        :key="index"
        class="w-[14.2%] bg-[#F3F3F4] overflow-hidden"
      >
        <div
          class="px-5 py-3 transition duration-300 transform hover:scale-110 cursor-pointer"
        >
          <img
            class="w-full h-full object-cover"
            :src="partner.image"
            :alt="partner.name"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const partners = [
  {
    id: 1,
    name: "Zapier",
    image:
      "https://e7.pngegg.com/pngimages/296/156/png-clipart-zapier-black-logo-tech-companies.png",
  },
  {
    id: 2,
    name: "Spotify",
    image:
      "https://w7.pngwing.com/pngs/803/51/png-transparent-spotify-hd-logo.png",
  },
  {
    id: 3,
    name: "Zoom",
    image:
      "https://joyfullearningcenter.com/wp-content/uploads/2020/05/zoom-logo.png",
  },
  {
    id: 4,
    name: "Amazon",
    image:
      "https://upload.wikimedia.org/wikipedia/commons/a/a9/Amazon_logo.svg",
  },
  {
    id: 5,
    name: "Adobe",
    image:
      "https://upload.wikimedia.org/wikipedia/commons/8/8d/Adobe_Corporate_Logo.png",
  },
  {
    id: 6,
    name: "Notion",
    image:
      "https://i0.wp.com/get.site/wp-content/uploads/2021/10/notion-logo.png?ssl=1",
  },
  {
    id: 7,
    name: "Netflix",
    image: "https://logolook.net/wp-content/uploads/2021/11/Netflix-Logo.png",
  },
];
</script>
