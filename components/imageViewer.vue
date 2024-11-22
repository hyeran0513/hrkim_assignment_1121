<template>
  <div class="image-gallery__viewer">
    <img :src="image" alt="썸네일 이미지" />

    <button type="button" class="image-gallery__close-btn" @click="closeViewer">
      <i class="fa fa-times" aria-hidden="true"></i>
    </button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

const props = defineProps({
  image: String,
});

const emit = defineEmits(["close"]);

// 선택한 썸네일 뷰어 닫기
const closeViewer = () => {
  emit("close");
};
</script>

<style lang="scss" scoped>
@use "@/assets/scss/pages/20241122/assignment1.scss" as assignment1;
</style>