<template>
  <div class="container">
    <div v-for="(assignments, date) in data" :key="date" class="group">
      <div class="date">{{ date }}</div>

      <ul class="list">
        <li class="list-item" v-for="(item, index) in assignments" :key="index">
          <NuxtLink :to="item.link">{{ item.txt }}</NuxtLink>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
const data = ref({
  "2024.11.21": [
    { txt: "도전과제1", link: "/20241121/assignment1" },
    { txt: "도전과제2", link: "/20241121/assignment2" },
    { txt: "도전과제3", link: "/20241121/assignment3" }
  ],
  "2024.11.22": [
    { txt: "도전과제1", link: "/20241122/assignment1" },
    { txt: "도전과제2", link: "/20241122/assignment2" },
    { txt: "도전과제3", link: "/20241122/assignment3" },
    { txt: "도전과제4", link: "/20241122/assignment4" }
  ]
});
</script>

<style lang="scss" scoped>
@use "@/assets/scss/pages/index.scss";
</style>
