<template>
  <div class="page">
    <div class="container">
      <div class="select-btn">
        <span class="btn-text">
          <span v-if="selectedCount > 0">{{ selectedCount }} Selected</span>
          <span v-else>Select Language</span>
        </span>

        <button
          type="button"
          :title="showMenu ? '메뉴 접기' : '메뉴 펼치기'"
          class="arrow-down"
          :class="{ 'is-active': showMenu }"
          @click="showMenu = !showMenu"
        >
          <i class="fa-solid fa-chevron-down"></i>
        </button>
      </div>

      <transition name="slide">
        <ul class="list-items" v-show="showMenu">
          <li class="item" v-for="(item, index) in listData" :key="index">
            <span class="checkbox">
              <input
                type="checkbox"
                :id="`checkbox_${index}`"
                v-model="checkedItems[index]"
              />
              <label :for="`checkbox_${index}`">
                <span class="item-icon">
                  <i class="fa-solid fa-check check-icon"></i>
                </span>
                <span class="item-text">{{ item }}</span>
              </label>
            </span>
          </li>
        </ul>
      </transition>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const listData = ref([
  "HTML & CSS",
  "Bootstrap",
  "JavaScript",
  "Node.Js",
  "React JS",
  "Mongo DB",
]);

// 메뉴의 노출 여부
const showMenu = ref(false);

// 체크박스 항목들의 선택 상태
const checkedItems = ref(new Array(listData.value.length).fill(false));

// 체크된 항목의 개수 계산 로직
const selectedCount = computed(() => {
  return checkedItems.value.filter((item) => item).length;
});
</script>

<style lang="scss" scoped>
@use "@/assets/scss/pages/20241121/assignment1.scss" as assignment1;
</style>