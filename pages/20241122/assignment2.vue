<template>
  <div class="page">
    <div
      class="empty"
      v-for="(empty, index) in emptyItems"
      :key="index"
      @dragover.prevent
      @dragenter.prevent
      @drop="handleDrop(index)"
      :class="{ hovered: isHovered(index) }"
      @dragenter="handleDragEnter(index)"
      @dragleave="handleDragLeave(index)"
    >
      <div
        v-if="empty"
        class="fill"
        draggable="true"
        @dragstart="handleDragStart(index)"
        @dragend="handleDragEnd"
        :class="{ hold: isHeld(index) }"
      ></div>
    </div>
  </div>
</template>


<script setup>
import { ref } from "vue";

// 첫 번째 박스에만 fill을 넣고, 나머지는 비어있는 상태
const emptyItems = ref([true, false, false, false, false]);

const draggedIndex = ref(null);
const hoveredIndex = ref(null);

// 드래그 시작할 때, 해당 요소의 인덱스를 삽입
const handleDragStart = (index) => {
  draggedIndex.value = index;
};

// 드래그 종료 시, 초기화
const handleDragEnd = () => {
  draggedIndex.value = null;
  hoveredIndex.value = null;
};

// 드래그 중에 hover 상태 시, 해당 인덱스 삽입
const handleDragEnter = (index) => {
  hoveredIndex.value = index;
};

// 드래그가 박스를 벗어날 경우, hover 상태 초기화
const handleDragLeave = () => {
  hoveredIndex.value = null;
};

// 드래그를 드롭했을 때
const handleDrop = (dropIndex) => {
  // 드래그된 아이템이 있고 드롭 대상 박스가 비어 있는 경우
  if (
    draggedIndex.value !== null &&
    emptyItems.value[dropIndex] === false
  ) {
    emptyItems.value[dropIndex] = true;
    emptyItems.value[draggedIndex.value] = false;
  }
};

// 현재 인덱스가 hover 상태인지 확인
const isHovered = (index) => {
  hoveredIndex.value === index;
}

// 현재 드래그 중인 인덱스가 hold 상태인지 확인
const isHeld = (index) => {
  draggedIndex.value === index;
}
</script>

<style lang="scss" scoped>
@use "@/assets/scss/pages/20241122/assignment2.scss" as assignment2;
</style>