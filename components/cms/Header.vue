<template>
  <div class="bg-[#F3F3F4] w-full mx-auto">
    <div class="w-[98%] m-auto">
      <nuxt-link :to="form.linkTieuDe" class="mx-auto">
        <button
          class="tieuDe border-none py-3 text-base w-full mx-auto bg-[#5236ff] text-white rounded-md mt-4 hover:bg-sky-500 flex items-center cursor-pointer"
        >
          <div class="mx-auto">{{ form.tieuDe }}</div>
        </button>
      </nuxt-link>
      <div class="w-full flex relative">
        <!-- <div class="w-[10%]"></div> -->
        <div class="w-[80%] mx-auto flex py-3">
          <div class="flex items-center justify-between w-full">
            <div class="flex items-center">
              <div class="logo ml-5">
                <img :src="form.logo" alt="Logo" class="w-40 h-20 px-4 py-4" />
              </div>
              <div class="text-base ml-8" v-for="menu in menus" :key="menu.id">
                <nuxt-link :to="menu.link">{{ menu.name }}</nuxt-link>
              </div>
              <div class="ml-5 flex">
                <div class="text-base mt-1">
                  <nuxt-link to="#">
                    <img
                      class="w-5 h-5"
                      src="https://cdn-icons-png.flaticon.com/512/1170/1170627.png"
                    />
                  </nuxt-link>
                </div>
              </div>
            </div>
            <div class="ml-4 mr-10">
              <nuxt-link :to="form.linkDangNhap" class="text-base mr-7">{{
                form.dangNhap
              }}</nuxt-link>
              <nuxt-link
                :to="form.linkDangKy"
                class="bg-[#5236ff] py-3 px-7 border-none rounded-md cursor-pointer text-white hover:bg-sky-500"
                >{{ form.dangKy }}</nuxt-link
              >
            </div>
          </div>
        </div>
        <div class="absolute right-0 top-1/2 transform -translate-y-1/2">
          <n-button
            @click="editMode = true"
            type="success"
            class="bg-green-600 px-6 py-3 mr-4"
          >
            Sửa
          </n-button>
        </div>
      </div>
    </div>
    <n-modal v-model:show="editMode">
      <n-card
        style="width: 600px"
        title="Chỉnh sửa"
        :bordered="false"
        size="huge"
        role="dialog"
        aria-modal="true"
      >
        <template #header-extra></template>
        <div class="w-full">
          <div class="bg-white p-8 pr-0 rounded-lg">
            <div class="mb-4">
              <label for="editTitle" class="block font-semibold"
                >Tiêu đề:</label
              >
              <div class="flex items-center">
                <div class="flex-1">
                  <input
                    type="text"
                    id="editTitle"
                    class="w-full border rounded p-2 border-gray-500"
                    v-model="editData.editTieuDe"
                    @keydown.enter.prevent="handleEnterKey"
                  />
                  <label for="editSubtitle" class="block font-semibold"
                    >Link:</label
                  >
                  <input
                    id="editSubtitle"
                    type="text"
                    v-model="editData.editLinkTieuDe"
                    class="w-full border rounded p-2 border-gray-500"
                    :placeholder="'Nhập link'"
                    @keydown.enter.prevent="handleEnterKey"
                  />
                </div>
              </div>
            </div>
            <div class="mb-4">
              <label for="editBackground" class="block font-semibold"
                >Logo:</label
              >
              <div class="flex items-center">
                <input
                  type="file"
                  id="editLogo"
                  accept="image/*"
                  class="w-full border rounded p-2 border-gray-500"
                  @change="handleEditLogo"
                  @keydown.enter.prevent="handleEnterKey"
                />
              </div>
            </div>
            <div class="mb-4 space-y-3">
              <label for="editSubtitle" class="block font-semibold"
                >Menu:</label
              >
              <n-collapse
                arrow-placement="right"
                v-for="item in editData.editMenus"
                :key="item.id"
                class="mt-2 flex items-center"
              >
                <n-collapse-item
                  class="flex-1"
                  :title="item.editName"
                  :name="item.id"
                >
                  <label for="editSubtitle" class="block font-semibold">
                    {{ item.editName }}</label
                  >
                  <input
                    id="editSubtitle"
                    type="text"
                    v-model="item.editName"
                    class="w-full border rounded p-2 border-gray-500"
                    :placeholder="'Nhập tên menu ' + item.editName"
                    @keydown.enter.prevent="handleEnterKey"
                  />
                  <label for="editSubtitle" class="block font-semibold"
                    >Link:</label
                  >
                  <input
                    id="editSubtitle"
                    type="text"
                    v-model="item.editLink"
                    class="w-full border rounded p-2 border-gray-500"
                    :placeholder="'Nhập link ' + item.editName"
                    @keydown.enter.prevent="handleEnterKey"
                  />
                </n-collapse-item>
                <button @click="remove(item.id)" class="self-start mt-0">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    xmlns:xlink="http://www.w3.org/1999/xlink"
                    viewBox="0 0 48 48"
                    class="w-8 h-8 text-red-500 items-center ml-2 mt-1"
                  >
                    <g fill="none">
                      <path
                        d="M24 6.75a6.25 6.25 0 0 1 6.246 6.02l.004.231L37 13a1.75 1.75 0 0 1 .144 3.494L37 16.5h-1.167l-1.627 21.57A4.25 4.25 0 0 1 29.968 42H18.032a4.25 4.25 0 0 1-4.238-3.93L12.166 16.5H11a1.75 1.75 0 0 1-1.744-1.607l-.006-.143a1.75 1.75 0 0 1 1.607-1.744L11 13h6.75c0-3.298 2.555-6 5.794-6.234l.227-.012L24 6.75zm3.75 13a1.25 1.25 0 0 0-1.244 1.122L26.5 21v12l.006.128a1.25 1.25 0 0 0 2.488 0L29 33V21l-.006-.128a1.25 1.25 0 0 0-1.244-1.122zm-7.5 0a1.25 1.25 0 0 0-1.244 1.122L19 21v12l.006.128a1.25 1.25 0 0 0 2.488 0L21.5 33V21l-.006-.128a1.25 1.25 0 0 0-1.244-1.122zm3.918-9.495L24 10.25a2.75 2.75 0 0 0-2.745 2.582l-.005.169l5.5-.001a2.75 2.75 0 0 0-2.582-2.745z"
                        fill="currentColor"
                      ></path>
                    </g>
                  </svg>
                </button>
              </n-collapse>
            </div>
            <div class="mt-2">
              <label for="editSubtitle" class="block font-semibold">{{
                editData.editDangNhap
              }}</label>
              <input
                id="editSubtitle"
                type="text"
                v-model="editData.editDangNhap"
                class="w-full border rounded p-2 border-gray-500"
                :placeholder="editData.editDangNhap"
                @keydown.enter.prevent="handleEnterKey"
              />
              <label for="editSubtitle" class="block font-semibold">Link</label>
              <input
                id="editSubtitle"
                type="text"
                v-model="editData.editLinkDangNhap"
                class="w-full border rounded p-2 border-gray-500"
                :placeholder="'Nhập link ' + editData.editDangNhap"
                @keydown.enter.prevent="handleEnterKey"
              />
            </div>

            <div class="mt-2 mb-8">
              <label for="editSubtitle" class="block font-semibold">{{
                editData.editDangKy
              }}</label>
              <input
                id="editSubtitle"
                type="text"
                v-model="editData.editDangKy"
                class="w-full border rounded p-2 border-gray-500"
                :placeholder="editData.editDangKy"
                @keydown.enter.prevent="handleEnterKey"
              />
              <label for="editSubtitle" class="block font-semibold">Link</label>
              <input
                id="editSubtitle"
                type="text"
                v-model="editData.editLinkDangKy"
                class="w-full border rounded p-2 border-gray-500"
                :placeholder="'Nhập link ' + editData.editDangKy"
                @keydown.enter.prevent="handleEnterKey"
              />
            </div>
          </div>
        </div>

        <template #footer>
          <div class="text-right mt-0">
            <button
              class="px-4 py-2 bg-blue-400 text-white rounded hover:bg-blue-600"
              @click="saveChanges"
            >
              Lưu
            </button>
            <button
              class="px-4 py-2 bg-gray-300 text-gray-800 rounded ml-2 hover:bg-gray-500"
              @click="cancelEdit"
            >
              Hủy
            </button>
          </div>
          <div class="mt-4">
            <n-button
              class="bg-green-600 px-6 py-3"
              @click="editAdd = true"
              type="success"
            >
              Thêm
            </n-button>
          </div>
        </template>

        <div class="w-full">
          <n-modal v-model:show="editAdd">
            <n-card
              style="width: 600px"
              title="Thêm mới"
              :bordered="false"
              size="huge"
              role="dialog"
              aria-modal="true"
            >
              <template #header-extra> </template>
              <div class="h-full pr-8 overflow-y-auto">
                <div class="mb-4">
                  <!-- <b class="flex text-2xl text-green-500 items-center"
                    >Thêm mới menu</b
                  > -->
                  <div class="mb-4">
                    <label
                      for="menuName"
                      class="block text-gray-800 font-semibold"
                      >Tên menu:</label
                    >
                    <input
                      type="text"
                      id="menuName"
                      v-model="newMenuName"
                      class="w-full border rounded p-2 border-gray-500"
                      placeholder="Nhập tên menu"
                      @keydown.enter.prevent="handleEnterKey"
                    />
                  </div>
                  <div class="mb-6">
                    <label
                      for="menuLink"
                      class="block text-gray-800 font-semibold"
                      >Liên kết:</label
                    >
                    <input
                      type="text"
                      id="menuLink"
                      v-model="newMenuLink"
                      class="w-full border rounded p-2 border-gray-500"
                      placeholder="Nhập đường dẫn menu"
                      @keydown.enter.prevent="handleEnterKey"
                    />
                  </div>
                </div>
              </div>
              <template #footer>
                <div class="text-center">
                  <button
                    @click="addNewMenu"
                    class="bg-blue-500 hover:bg-blue-600 text-white font-semibold py-2 px-6 rounded-md mr-3"
                  >
                    Thêm mới
                  </button>
                  <button
                    @click="editAddNewMenu"
                    class="bg-gray-500 hover:bg-gray-600 text-white font-semibold py-2 px-6 rounded-md"
                  >
                    Hủy
                  </button>
                </div>
              </template>
            </n-card>
          </n-modal>
        </div>
      </n-card>
    </n-modal>
  </div>
</template>

<script setup>
import { ref, defineComponent } from "vue";
import {
  useMessage,
  NCollapse,
  NCollapseItem,
  NButton,
  NCard,
  NModal,
  NInput,
} from "naive-ui";

const message = useMessage();

// export default defineComponent({
//   setup() {
//     return {
//       value: ref(null),
//     };
//   },
// });

const editMode = ref(false);
const form = ref({
  tieuDe: "Khóa học giao tiếp Ưu đãi sắp kết thúc. Mua ngay",
  linkTieuDe: "",
  logo: "https://static.ladipage.net/5b33575d031f5281797296b9/mschool-20201019033206.png",
  dangNhap: "Đăng nhập",
  linkDangNhap: "",
  dangKy: "Đăng ký",
  linkDangKy: "",
});

let temporaryLogo;

const menus = ref([
  { id: 1, name: "Trang chủ", link: "/" },
  { id: 2, name: "Tin tức", link: "" },
  { id: 3, name: "Khóa học", link: "/khoa-hoc" },
  { id: 4, name: "Kích hoạt khóa học", link: "" },
  { id: 5, name: "Liên hệ", link: "" },
]);

const editData = ref({
  editTieuDe: form.value.tieuDe,
  editLinkTieuDe: form.value.linkTieuDe,
  editLogo: form.value.logo,
  editDangNhap: form.value.dangNhap,
  editLinkDangNhap: form.value.linkDangNhap,
  editDangKy: form.value.dangKy,
  editLinkDangKy: form.value.linkDangKy,
  editMenus: [],
});

menus.value.forEach((menu, index) => {
  editData.value.editMenus.push({
    id: menu.id,
    editName: menu.name,
    editLink: menu.link,
  });
});

const saveChanges = () => {
  editMode.value = false;
  temporaryLogo = null;
  form.value.tieuDe = editData.value.editTieuDe;
  form.value.linkTieuDe = editData.value.editLinkTieuDe;
  form.value.logo = editData.value.editLogo;
  form.value.dangNhap = editData.value.editDangNhap;
  form.value.linkDangNhap = editData.value.editLinkDangNhap;
  form.value.dangKy = editData.value.editDangKy;
  form.value.linkDangKy = editData.value.editLinkDangKy;
  menus.value = [];
  editData.value.editMenus.forEach((menu, index) => {
    menus.value.push({
      id: menu.id,
      name: menu.editName,
      link: menu.editLink,
    });
  });
  message.success("Lưu thành công");
};

const cancelEdit = () => {
  editMode.value = false;
  editData.value.editTieuDe = form.value.tieuDe;
  editData.value.editLinkTieuDe = form.value.linkTieuDe;
  editData.value.editLogo = form.value.logo;
  editData.value.editDangNhap = form.value.dangNhap;
  editData.value.editLinkDangNhap = form.value.linkDangNhap;
  editData.value.editDangKy = form.value.dangKy;
  editData.value.editLinkDangKy = form.value.linkDangKy;
  editData.value.editMenus = [];
  menus.value.forEach((menu, index) => {
    editData.value.editMenus.push({
      id: menu.id,
      editName: menu.name,
      editLink: menu.link,
    });
  });
};

const handleEditLogo = (event) => {
  const file = event.target.files[0];
  if (file) {
    const reader = new FileReader();
    reader.onload = (e) => {
      editData.value.editLogo = e.target.result;
    };
    reader.readAsDataURL(file);
  }
};

const handleEnterKey = (event) => {
  if (event.key === "Enter") {
    saveChanges();
    addNewMenu();
  }
};

const editAdd = ref(false);

const newMenuName = ref("");
const newMenuLink = ref("");

function editAddNewMenu() {
  newMenuName.value = "";
  newMenuLink.value = "";
  editAdd.value = false;
}

function addNewMenu() {
  if (newMenuName.value && newMenuLink.value) {
    editData.value.editMenus = [
      ...editData.value.editMenus,
      {
        id: editData.value.editMenus.length + 1,
        editName: newMenuName.value,
        editLink: newMenuLink.value,
      },
    ];

    newMenuName.value = "";
    newMenuLink.value = "";
  }
  message.success("Thêm mới thành công");

  editAdd.value = false;
}

function remove(id) {
  // console.log("id ", id);
  editData.value.editMenus = editData.value.editMenus.filter(function (item) {
    return item.id !== id;
  });
  // console.log(
  //   editData.value.editMenus.filter(function (item) {
  //     return item.id !== id;
  //   })
  // );
  // console.log(editData.value.editMenus);
}

// const deleteSection = () => {
//   const elementToDelete = document.querySelector(".tieuDe");
//   if (elementToDelete) {
//     elementToDelete.remove();
//   }
// };

// const deletelogo = () => {
//   const elementToDelete = document.querySelector(".logo");
//   if (elementToDelete) {
//     elementToDelete.remove();
//   }
// };
</script>
