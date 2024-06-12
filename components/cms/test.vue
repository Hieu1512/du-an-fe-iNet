<template>
  <n-button @click="submit"> Thêm mới </n-button>
  <!-- <n-modal
    v-model:show="showModal"
    preset="dialog"
    title="Dialog"
    positive-text="Submit"
    positive-color="green"
    negative-text="Cancel"
    @positive-click="submit"
    @negative-click="cancel"
  /> -->
</template>

<script setup>
import { ref, defineComponent } from "vue";
import { useMessage, NButton, NModal } from "naive-ui";

const showModal = ref(false);
const message = useMessage();

const cancel = () => {
  message.success("Cancel");
  showModal.value = false;
};

const submit = () => {
  message.success("Submit");
  showModal.value = false;
};
</script>
