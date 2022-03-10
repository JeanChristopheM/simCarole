//. SCRIPT .
<script setup lang="ts">
import { ref } from "vue";
const mobileMenuToggle = ref(false);
const menuLinks = ref(["DESTINATION", "LE WEEKEND", "LOGEMENT"]);
const handleClick = (e: MouseEvent) => {
  e.preventDefault();
  const target = e.target as HTMLElement;
  const id = target?.id;
  const element = document.querySelector(`.${id}`);
  if (!element) return;
  const rect = element.getBoundingClientRect();
  const x = rect.x;
  const y = rect.y;
  window.scrollTo(x, y);
  mobileMenuToggle.value = !mobileMenuToggle.value;
};
</script>
//. TEMPLATE .
<template>
  <header class="header">
    <nav class="header__nav mobile">
      <button
        type="button"
        class="header__nav__link mobileMenuBtn"
        @click="mobileMenuToggle = !mobileMenuToggle"
      >
        MENU
      </button>
      <div :class="`mobileMenu ${mobileMenuToggle ? 'active' : ''}`">
        <div class="mobileMenu__linksContainer">
          <a
            v-for="link in menuLinks"
            class="header__nav__link"
            :id="link.toLowerCase()"
            @click="handleClick"
            >{{ link }}</a
          >
        </div>
      </div>
    </nav>
    <nav class="header__nav desktop">
      <a
        v-for="link in menuLinks"
        :id="link.toLowerCase()"
        @click="handleClick"
        class="header__nav__link"
        >{{ link }}</a
      >
    </nav>
  </header>
</template>
