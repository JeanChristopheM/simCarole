<script setup lang="ts">
import { ref } from "vue";
import Map from "./Map.vue";
import BgSvg from "./BgSvg.vue";
const src = ref(
  "https://images.unsplash.com/photo-1548625149-fc4a29cf7092?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1964&q=80"
);
</script>
<template>
  <section class="destination" id="destination" name="destination">
    <div class="destination__bgContainer backgroundImageContainer">
      <BgSvg
        className="destination__bgContainer-bg backgroundImageContainer__image"
      />
    </div>
    <h2 class="sectionTitle">DESTINATION</h2>
    <div class="location">
      <figure class="figure">
        <img :src="src" alt="church" class="circleImage" />
        <figcaption>L'église</figcaption>
      </figure>
      <p>L'église de notre dame, à Woluwe</p>
      <p>
        Nous avons décidé de nous Lorem ipsum, dolor sit amet consectetur
        adipisicing elit. Nesciunt, laborum.
      </p>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Aut omnis
        repudiandae ipsum quia placeat tempora mollitia est! Sapiente,
        asperiores fugit quaerat eveniet obcaecati assumenda iusto?
      </p>
    </div>
    <div class="gettingThere">
      <h3 class="sectionSubTitle">S'Y RENDRE</h3>
      <Map />
    </div>
  </section>
</template>
