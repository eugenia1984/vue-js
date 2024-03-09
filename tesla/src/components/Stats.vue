<template>
  <div class="stats bg-cover bg-no-repeat bg-bottom" :style="`background-image: url(${TeslaBackground}); height: 450px;`">
    <div class="w-full h-full bg-blue-950 opacity-75 absolute z-0" />
    <div class="stats-components z-50 relative">
      <p class="text-white">some text</p>
    </div>
  </div>
</template>

<script setup>
import { StatsCard } from "./index";
import TeslaBackground from "../assets/tesla-background.jpg";


</script>
