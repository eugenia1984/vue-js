<template>
  <section class="tabs">
    <header class="flex flex-col md:flex-row items-center justify-center mb-4">
      <div 
        v-for="obj, objIndex in tabs" :key="objIndex" class="tabs-header-item px-6 py-4 mx-3 cursor-pointer" 
        :class="objIndex === activeTab ? 'text-blue-800 border-b-4 border-blue-800' : 'border-b'" 
        @click="updateActiveTab(objIndex)">
        {{ obj.title }}
      </div>
    </header>
    <section class="container mx-auto">
      <section 
        class="container mx-auto bg-blue-950 rounded-md text-white bg-contain bg-no-repeat flex items-center justify-center px-3" 
        :style="`min-height: 500px;`">
        <div class="mb-16 px-8">
          <h2 class="text-4xl uppercase font-bold mb-4">{{ getActiveTabContent.title}}</h2>
          <p v-html="getActiveTabContent.description" />
        </div>
      </section>
    </section>
  </section>
</template>

<script>
import { reactive, toRefs, computed } from "vue";
import Inside from "../assets/tesla-tab.png";

export default {
  setup() {
    const data = reactive({
      activeTab: 0,
      getActiveTabContent: computed(() => {
        return data.tabs[data.activeTab]
      }),
      tabs: [
        {
          imgSrc: Inside,
          title: 'Design',
          description: '<strong>Cinematic Experience: </strong>A 17” touchscreen with left-right tilt offers 2200 x 1300 resolution, true colors and exceptional responsiveness for gaming, movies and more.</br></br><strong>Perfect Environment: </strong> Air vents are hidden throughout the cabin, while tri-zone temperature controls, ventilated seats and HEPA filtration deliver the perfect environment.</br></br><strong>Stay Connected: </strong>Instantly connect with multi-device Bluetooth, or fast charge devices with wireless and 36-watt USB-C charging.'
        },
        {
          imgSrc: Inside,
          title: 'Performance',
          description: '<strong>Designed for Efficiency: </strong>With a drag coefficient of just .208 Cd, the lowest on the planet, Model S is built for speed, endurance and range. Improved aerodynamics and a wider chassis offer more responsive performance so you can take corners quicker and with more confidence.</br></br><strong>Relentless Performance: </strong> Staggered, performance wheels and tires keep the car planted and help transfer maximum power down to the road.'
        },
        {
          imgSrc: Inside,
          title: 'Safety',
          description: '<strong>High Impact Protection: </strong> Model S is built from the ground up as an electric vehicle, with a high-strength architecture and floor-mounted battery pack for incredible occupant protection and low rollover risk. Every new Model S includes Tesla’s latest active safety features, such as Automatic Emergency Braking, at no extra cost.'
        },
        {
          imgSrc: Inside,
          title: 'Comfort',
          description: '<strong>Room for Everything: </strong> with front and rear trunks and fold-flat seats you can fit your bike without taking the wheel off—and your luggage too.</br></br><strong>Features: </strong> Enhanced Autopilot and Full Self-Driving capability introduce additional features and improve existing functionality to make your car more capable over time, including: navigate on autopilot, auto lane change, summon and autopark.'
        }
      ]
    })

    const updateActiveTab = (objIndex) => {
      data.activeTab = objIndex
    }

    return {
      updateActiveTab,
      ...toRefs(data)
    }
  }
}
</script>