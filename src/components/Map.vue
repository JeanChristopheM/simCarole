<script lang="ts" setup>
import { onMounted } from "vue";

console.log(window);
onMounted(() => {
  //* Making sure the map does not exist yet .
  const container = document.querySelector(".mapContainer");
  if (container?.querySelector("#map")) return;
  //* Creating the map div .
  let mapDiv = document.createElement("div");
  mapDiv.id = "map";
  container?.append(mapDiv);
  //* Initializing the map .
  //@ts-ignore
  const map = L.map("map").setView([50.632557, 5.579666], 10);
  const attribution =
    '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors';
  const tileUrl = "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png";
  //@ts-ignore
  const tiles = L.tileLayer(tileUrl, { attribution });
  tiles.addTo(map);
  //* Adding marker
  //@ts-ignore
  var marker = L.marker([50.84673, 4.35247]).addTo(map);
});
</script>

<template>
  <div class="mapContainer"></div>
</template>
<script lang="ts">
import "../assets/leaflet";
</script>

<style lang="scss"></style>
