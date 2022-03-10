//. SCRIPT .
<script setup lang="ts">
import { onBeforeUnmount, onMounted, Ref, ref } from "vue";
import BgSvg from "./BgSvg.vue";
const svg: Ref<SVGElement | undefined> = ref();
let svgWidth = ref();
let svgHeight = ref();
onMounted(() => {
  svgWidth.value = svg.value?.getBoundingClientRect().width;
  svgHeight.value = svg.value?.getBoundingClientRect().height;
  const mediaQuery = window.matchMedia("(min-width: 500px)");
  mediaQuery.onchange = () => {
    if (svg.value === null) return;
    svgWidth.value = svg.value?.getBoundingClientRect().width;
    svgHeight.value = svg.value?.getBoundingClientRect().height;
  };
});
</script>
//. TEMPLATE .
<template>
  <section class="banner">
    <div class="banner__bgContainer backgroundImageContainer">
      <BgSvg
        className="banner__bgContainer-bg backgroundImageContainer__image"
      />
    </div>
    <div class="banner__content">
      <svg
        viewBow="0 0 300 300"
        xmlns="http://www.w3.org/2000/svg"
        class="svg"
        ref="svg"
      >
        <text
          v-if="svgWidth"
          x="0"
          :y="svgHeight / 2"
          textLength="1rem"
          class="svg__text"
          text-anchor="start"
          dominant-baseline="middle"
        >
          S
        </text>
        <rect
          v-if="svgWidth"
          x="32"
          :y="svgHeight / 2 - 3"
          :width="svgWidth - 70"
          height="2"
          class="svg__bar"
        />
        <text
          v-if="svgWidth"
          :x="svgWidth - 2"
          :y="svgHeight / 2"
          textLength="1rem"
          text-anchor="end"
          dominant-baseline="middle"
          class="svg__text"
        >
          C
        </text>
      </svg>
      <h1 class="fancyFont">simon & carole</h1>
      <h3><a href="http://ameliaandsteve.com/">SE MARIENT !</a></h3>
      <div class="scroll">
        <p>DESCENDEZ POUR EN SAVOIR PLUS</p>
        <p id="arrow">&darr;</p>
      </div>
    </div>
  </section>
</template>
