<template>
  <div>
    <NuxtLink v-for="(item, index) in data" :to="item.link" :key="index">
      {{ item.txt }}
    </NuxtLink>
  </div>
</template>

<script setup>
const data = ref([
  { txt: "도전과제1", link: "/assignment1" },
  { txt: "도전과제2", link: "/assignment2" },
  { txt: "도전과제3", link: "/assignment3" },
]);
</script>

<style lang="scss" scoped>
</style>
