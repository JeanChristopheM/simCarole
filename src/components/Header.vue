<script setup lang="ts">
import { ref } from "vue";
const mobileMenuToggle = ref(false);
const handleMobileMenuBtn = (e: MouseEvent) => {
  mobileMenuToggle.value = mobileMenuToggle.value === false ? true : false;
};
const menuLinks = ref(["DESTINATION", "LE WEEKEND", "LOGEMENT"]);
</script>
<template>
  <header class="header">
    <nav class="header__nav mobile">
      <button
        type="button"
        class="header__nav__link mobileMenuBtn"
        @click="handleMobileMenuBtn"
      >
        MENU
      </button>
      <div class="mobileMenu">
        <div class="mobileMenu__linksContainer">
          <a v-for="link in menuLinks" class="header__nav__link">{{ link }}</a>
        </div>
      </div>
    </nav>
    <nav class="header__nav desktop">
      <a v-for="link in menuLinks" class="header__nav__link">{{ link }}</a>
    </nav>
  </header>
</template>
