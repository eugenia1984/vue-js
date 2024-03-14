<template>
  <div class="nav container mx-auto my-8 grid grid-flow-col grid-cols-1 md:grid-cols-3 gap-4">
    <div>
      <img :src="Logo" width="56" height="56" alt="Tesla logo in black and white" class="w-14 mx-auto md:mx-0" />
    </div>
    <div class="hidden md:grid col-span-3">
      <div class="grid grid-flow-col grid-cols-4 gap-4 items-center justify-items-center h-full">
        <a
          v-for="(option, optionIndex) in menu"
          :key="optionIndex"
          href={{option.link}}
          target="_blank"
          class="cursor-pointer text-sm font-bold hover:text-white hover:bg-blue-900 px-8 py-2"
        >
          {{ option.title }}
        </a>
      </div>
    </div>
    <div class="grid col-span-3 md:hidden fixed right-8 top-8 cursor-pointer">
      <button @click="openLink('https://www.linkedin.com/in/maria-eugenia-costa/')">
        <img :src="Menu" width="56" height="56" alt="Menu icon in black and white" class="w-8" />
      </button>
    </div>
  </div>
</template>

<script setup>
import Logo from "../assets/tesla-icon.png";
import Menu from "../assets/menu.png";

const menu = [
  { title: "Model S", link: "https://www.linkedin.com/in/maria-eugenia-costa/" },
  { title: "Model 3", link: "https://www.linkedin.com/in/maria-eugenia-costa/" },
  { title: "Model X", link: "https://www.linkedin.com/in/maria-eugenia-costa/" },
  { title: "Model Y",  link: "https://www.linkedin.com/in/maria-eugenia-costa/" }
];

const openLink = (link) => {
  window.open(link);
};
</script>
