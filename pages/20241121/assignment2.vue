<template>
  <div class="page">
    <div class="container">
      <div class="card" v-for="(item, index) in data" :key="index">
        <div class="card-item">
          <img :src="item.thumb" :alt="item.title" />

          <div class="details">
            <p class="title">{{ item.title }}</p>
            <div class="content">{{ item.content }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import artist01 from "@/assets/images/20241121/assignment2/artist-01.jpg";
import artist02 from "@/assets/images/20241121/assignment2/artist-02.jpg";
import artist03 from "@/assets/images/20241121/assignment2/artist-03.jpg";

const data = ref([
  {
    thumb: artist01,
    title: "Photographer",
    content:
      "AS in other arts, the definitions of amateur and professional are not entirely categorical.",
  },
  {
    thumb: artist02,
    title: "Musician",
    content: "A composer is a musician who creates musical compositions.",
  },
  {
    thumb: artist03,
    title: "Sculptor",
    content:
      "Sculpture is the branch of the visual arts that operates in three dimensions.",
  },
]);
</script>

<style lang="scss" scoped>
@use "@/assets/scss/pages/20241121/assignment2.scss" as assignment2;
</style>