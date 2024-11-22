<template>
  <div class="page">
    <div class="toggle" :class="toggleClass" @click="toggleState">
      <span class="circle"></span>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

// 토글 상태
const isToggled = ref(false);

// 토글 상태에 따라 적용될 클래스명
const toggleClass = computed(() => {
  return isToggled.value ? "toggle--active" : "toggle--inactive";
});

// 토글 상태 반전
const toggleState = () => {
  isToggled.value = !isToggled.value;
};
</script>

<style lang="scss" scoped>
@use "@/assets/scss/pages/20241122/assignment3.scss" as assignment3;
</style>