<template>
  <section class="stats-card flex flex-col items-center justify-start text-black text-center bg-white p-16 shadow-lg">
    <img class="h-16 mb-8" :src="content.imgSrc" :alt="content.title">
    <h2 class="text-xl font-light mb-2">{{ content.title }}</h2>
    <p class="font-bold text-sm" v-html="content.description" />
  </section>
</template>

<script>
import GeneralMixin from "../../../mixins/GeneralMixin";

export default {
  mixins: [GeneralMixin]
}
</script>

<style>
  .stats-card {
    min-width: 200px;
    max-width: 200px;
    min-height: 300px;
    max-height: 300px;
  }
</style>