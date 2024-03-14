<template>
  <div>
    <Nav class="container mx-auto" />
    <MainHeader class="container mx-auto"/>
    <Presentation v-for="obj, objIndex in presentations" :key="objIndex" :content="obj" class="mb-16"/>
    <Stats />
    <Tabs />
    <Footer class="container mx-auto" />
  </div>
</template>

<script>
import { MainHeader, Nav, Presentation, Stats, Tabs, Footer } from "../components";
import { reactive, toRefs } from "vue";
import ModelSInterior from "../assets/model-s-interior.jpg";


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
              title: 'Plaid',
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
              title: 'Exterior',
              subtitle: 'Designed for Efficiency',
              description: "With a drag coefficient of just .208 Cd, the lowest on the planet, Model S is built for speed, endurance and range. Improved aerodynamics and a wider chassis offer more responsive performance so you can take corners quicker and with more confidence.",
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
