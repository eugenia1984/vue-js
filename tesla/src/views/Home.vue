<template>
  <div>
    <Nav />
    <MainHeader />
    <Presentation v-for="obj, objIndex in presentations" :key="objIndex" :content="obj" />
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
              backgroundColor: 'bg-blue-900',
              title: 'Model S',
              subtitle: 'Beyond Ludicrous',
              description: "Model S Plaid has the quickest acceleration of any vehicle in production. Updated battery architecture for all Model S trims enables back-to-back track runs without performance degradation. Chat with a Tesla Advisor to learn more about Model S or schedule a demo drive today.",
            },
            {
              imgSrc: ModelSInterior
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
