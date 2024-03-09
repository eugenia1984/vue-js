<template>
  <div class="stats bg-cover bg-no-repeat bg-bottom" :style="`background-image: url(${TeslaBackground}); height: 450px;`">
    <div class="w-full h-full bg-blue-950 opacity-75 absolute z-0" />
    <div class="stats-components z-50 relative container mx-auto">
      <p class="text-white">{{ cards }}</p>
      <StatsCard v-for="obj, objIndex in cards" :key="objIndex" :content="obj"/>
    </div>
  </div>
</template>

<script>
import { reactive, toRefs } from "vue";
import { StatsCard } from "./index";
import Plug from "../assets/rounded-plug.png";
import Speed from "../assets/speed.png";
import Size from "../assets/dimensions.png";
import Weight from "../assets/weight.png";
import TeslaBackground from "../assets/tesla-background.jpg";

export default {
  components: {
    StatsCard 
  },
  setup() {
    const data = reactive({
      TeslaBackground,
      cards: [
        {
          imgSrc: Plug,
          title: 'Range',
          description: 'miles'
        },
        {
          imgSrc: Speed,
          title: 'Speed',
          description: ' s'
        },
        {
          imgSrc: Size,
          title: 'Size',
          description: 'xxxx'
        },
        {
          imgSrc: Weight,
          title: 'Weight',
          description: 'kg'
        }
      ]
    })

    return {
      ...toRefs(data)
    }
  }
}
</script>
