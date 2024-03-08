<template>
  <div class="nav container mx-auto my-8 grid grid-flow-col grid-cols-2 gap-4">
    <img :src="Logo" alt="Tesla logo in black and white" class="w-16" />
    <div class="hidden md:block">
      <div class="grid grid-flow-col grid-cols-4 gap-4 items-center">
      <p
        v-for="(option, optionIndex) in menu"
        :key="optionIndex"
        @click="openLink(option.link)"
        class="cursor-pointer text-sm font-bold"
      >
        {{ option.title }}
      </p>
    </div>
    </div>
  </div>
</template>

<script setup>
import Logo from "../assets/tesla-icon.png";

const menu = [
  {
    title: "Brand",
    link: "",
  },
  {
    title: "Brand 2",
    link: "",
  },
  {
    title: "Brand 3",
    link: "",
  },
  {
    title: "Brand 4",
    link: "",
  },
];

const openLink = (link) => {
  window.open(link);
};
</script>
