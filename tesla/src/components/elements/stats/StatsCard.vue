<template>
  <section class="stats-card text-black text-center">
    <h2 class="text-xl font-bold mb-2">{{ content.title }}</h2>
    <p class="font-light mb-4">{{ content.description }} </p>
  </section>
</template>

<script>
import GeneralMixin from "../../../mixins/GeneralMixin";

export default {
  mixins: [GeneralMixin]
}
</script>