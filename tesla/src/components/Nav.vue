<template>
  <div class="nav container mx-auto my-8 grid grid-flow-col grid-cols-1 md:grid-cols-4 gap-4">
    <div>
      <img :src="Logo" width="56" height="56" alt="Tesla logo in black and white" class="w-14 mx-auto md:mx-0" />
    </div>
    <div class="hidden md:grid col-span-3">
      <div class="grid grid-flow-col grid-cols-5 gap-4 items-center h-full">
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
    <div class="grid col-span-3 md:hidden fixed right-8 top-8 cursor-pointer">
      <img :src="Menu" width="56" height="56" alt="Menu icon in black and white" class="w-8" />
    </div>
  </div>
</template>

<script setup>
import Logo from "../assets/tesla-icon.png";
import Menu from "../assets/menu.png";

const menu = [
  { title: "Model S", link: "" },
  { title: "Model 3", link: "" },
  { title: "Model X", link: "" },
  { title: "Model Y",  link: "" },
  { title: "cybertruck",  link: "" }
];

const openLink = (link) => {
  window.open(link);
};
</script>
