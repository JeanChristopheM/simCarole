<script setup lang="ts">
import { ref, computed } from "vue";
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Home from "./components/Home.vue";

const routes: {
  [key: string]: JSX.Element;
} = {
  //@ts-ignore
  "/": Home,
};

const currentPath = ref(window.location.hash);

window.addEventListener("hashchange", () => {
  currentPath.value = window.location.hash;
});

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || "/"] || "NotFound";
});
</script>

<template>
  <Header />
  <main class="main">
    <component :is="currentView" />
  </main>
  <Footer />
</template>
