<template>
  <div class="stats bg-cover bg-no-repeat bg-bottom relative py-8 lg:pt-32" :style="`background-image: url(${TeslaBackground}); min-height: 332px;`">
    <div class="w-full h-full bg-blue-950 opacity-75 absolute top-0 left-0 z-0" />
   <div class="container">
    <div class="stats-components mx-auto flex flex-col lg:flex-row items-center justify-center w-full z-50 relative lg:absolute px-2 gap-6 lg:gap-2">
      <StatsCard v-for="obj, objIndex in cards" :key="objIndex" :content="obj"/>
    </div>
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
