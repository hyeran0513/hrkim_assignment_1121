<template>
  <div class="image-gallery">
    <ImageGallery
      :thumbnails="thumbnails"
      @click-thumbnail="clickThumbnail"
    />
    
    <ImageViewer
      v-if="selectedThumbnail"
      :image="selectedThumbnail"
      @close="closeViewer"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
import image1 from "@/assets/images/20241122/assignment1/sample1.jpg";
import image2 from "@/assets/images/20241122/assignment1/sample2.jpg";
import image3 from "@/assets/images/20241122/assignment1/sample3.jpg";
import image4 from "@/assets/images/20241122/assignment1/sample4.jpg";

const thumbnails = ref([image1, image2, image3, image4]);
const selectedThumbnail = ref(null);

// 썸네일 클릭
const clickThumbnail = (image) => {
  selectedThumbnail.value = image;
};

// 선택한 썸네일 뷰어 닫기
const closeViewer = () => {
  selectedThumbnail.value = null;
};
</script>

<style lang="scss" scoped>
@use "@/assets/scss/pages/20241122/assignment1.scss" as assignment1;
</style>
