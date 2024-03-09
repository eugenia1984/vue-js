<template>
  <div>
    <Nav />
    <MainHeader />
    <Presentation v-for="obj, objIndex in presentations" :key="objIndex" :content="obj" class="mb-16"/>
    <!-- <Presentation oriented="right" /> -->
    <Stats />
    <Tabs />
    <Footer />
  </div>
</template>

<script>
import { MainHeader, Nav, Presentation, Stats, Tabs, Footer } from "../components";
import { reactive, toRefs} from 'vue'
import ModelSInterior from '../assets/model-s-interior.jpg'


export default {
  components: {
    MainHeader, 
    Nav, 
    Presentation, 
    Stats, 
    Tabs, 
    Footer
  },
  setup() {
    let data = reactive({
      presentations: [
        {
          left: true,
          columns: [
            {
              backgroundColor: 'blue-950',
              title: 'Model S',
              subtitle: 'Beyond Ludicrous',
              description: "Model S Plaid has the quickest acceleration of any vehicle in production. Updated battery architecture for all Model S trims enables back-to-back track runs without performance degradation. Chat with a Tesla Advisor to learn more about Model S or schedule a demo drive today.",
            },
            {
              imgSrc: ModelSInterior
            }
          ]
        },
        {
          left: false,
          columns: [
            {
              backgroundColor: 'blue-50',
              title: 'Model 3',
              subtitle: 'Reengineered',
              description: "Build for distance: Go up to 341 miles (EPA est.) on a single charge with updated exterior styling optimized for maximum aerodynamics.",
            },
            {
              imgSrc: ModelSInterior,
              contain: true
            }
          ]
        }
      ]
    })

    return {
      ...toRefs(data)
    }
  }
}
</script>
