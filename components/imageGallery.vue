<template>
  <div class="image-gallery__thumbnails">
    <div
      class="image-gallery__thumbnails-item"
      v-for="(thumbnail, index) in thumbnails"
      :key="index"
      @click="handleThumbnailClick(thumbnail)"
      :style="{ backgroundImage: `url(${thumbnail})` }"
    ></div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

const props = defineProps({
  thumbnails: Array,
});

const emit = defineEmits(["click-thumbnail"]);

// 썸네일 클릭
const handleThumbnailClick = (thumbnail) => {
  emit("click-thumbnail", thumbnail);
};
</script>

<style lang="scss" scoped>
@use "@/assets/scss/pages/20241122/assignment1.scss" as assignment1;
</style>