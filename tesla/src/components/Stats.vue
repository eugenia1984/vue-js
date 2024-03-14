<template>
  <section 
    class="stats container mx-auto bg-cover bg-no-repeat bg-bottom relative py-8 lg:py-32 mb-8 lg:mb-32" 
    :style="`background-image: url(${TeslaBackground}); min-height: 332px;`">
    <div class="w-full h-full bg-blue-950 opacity-75 absolute top-0 left-0 z-0" />
   <div class="container mx-auto">
    <div class="stats-components mx-auto flex flex-col md:flex-row items-center justify-center w-full z-50 relative lg:absolute px-2 gap-6 lg:gap-2">
      <div class="flex flex-col md:flex-row gap-4 w-2/3 lg:w-full flex-wrap justify-center items-center">
        <StatsCard v-for="obj, objIndex in cards" :key="objIndex" :content="obj"/>
      </div>
    </div>
   </div>
  </section>
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
          description: '402 miles'
        },
        {
          imgSrc: Speed,
          title: 'Top Speed',
          description: '130 mph'
        },
        {
          imgSrc: Size,
          title: 'Peak Power',
          description: '670 hp'
        },
        {
          imgSrc: Weight,
          title: 'Weight',
          description: '4,560 lbs'
        }
      ]
    })

    return {
      ...toRefs(data)
    }
  }
}
</script>
