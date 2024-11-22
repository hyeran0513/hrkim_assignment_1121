<template>
  <div class="page">
    <div class="sidebar" ref="sidebarRef">
      <div class="logo-details">
        <i class="bx bxl-c-plus-plus"></i>
      </div>

      <ul class="nav-links">
        <li v-for="(item, index) in navItems" :key="index">
          <a
            href="#"
            @click="toggleSubMenu(index)"
            :class="{ 'is-active': activeIndex === index }"
            :title="item.name"
          >
            <i :class="item.icon"></i>
          </a>

          <ul
            v-if="item.subMenu && activeIndex === index"
            class="sub-menu"
            :class="{ multi: item.subMenu.length > 1 }"
          >
            <li v-for="(subItem, subIndex) in item.subMenu" :key="subIndex">
              <a
                :class="{ link_name: subIndex === 0 }"
                href="#"
                :title="subItem"
              >
                {{ subItem }}
              </a>
            </li>
          </ul>
        </li>
      </ul>
    </div>

    <section class="home-section">
      <div class="home-content">
        <i class="bx bx-menu"></i>
        <span class="text">드롭다운 응용</span>
      </div>
    </section>
  </div>
</template>


<script setup>
import { onClickOutside } from "@vueuse/core";
import { ref } from "vue";

const navItems = [
  {
    name: "대시보드",
    icon: "bx bx-grid-alt",
    subMenu: ["카테고리1"],
  },
  {
    name: "카테고리2",
    icon: "bx bx-collection",
    subMenu: ["카테고리3", "HTML & CSS", "JavaScript", "PHP & MySQL"],
  },
  {
    name: "포스트",
    icon: "bx bx-book-alt",
    subMenu: ["포스트", "Web Design", "Login Form", "Card Design"],
  },
  {
    name: "포스트2",
    icon: "bx bx-pie-chart-alt-2",
    subMenu: ["포스트2"],
  },
  {
    name: "차트",
    icon: "bx bx-line-chart",
    subMenu: ["차트"],
  },
  {
    name: "플러그인",
    icon: "bx bx-plug",
    subMenu: ["플러그인", "UI Face", "Pigments", "Box Icons"],
  },
  {
    name: "익스플로러",
    icon: "bx bx-compass",
    subMenu: ["익스플로러"],
  },
  {
    name: "히스토리",
    icon: "bx bx-history",
    subMenu: ["히스토리"],
  },
  {
    name: "설정",
    icon: "bx bx-cog",
    subMenu: ["설정"],
  },
];

// 활성화된 메뉴의 인덱스
const activeIndex = ref(null);

// 서브 메뉴의 토글 이벤트
const toggleSubMenu = (index) => {
  activeIndex.value = activeIndex.value === index ? null : index;
};

// 사이드바 ref
const sidebarRef = ref();

// 사이드바 외부 클릭 시, 활성화된 서브 메뉴를 닫기
onClickOutside(sidebarRef, event => {
  activeIndex.value = null;
})
</script>


<style lang="scss" scoped>
@use "@/assets/scss/pages/20241121/assignment3.scss" as assignment3;
</style>