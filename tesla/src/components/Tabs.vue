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
        class="container mx-auto bg-contain bg-no-repeat flex items-center justify-center" 
        :style="`background-image: url(${getActiveTabContent.imgSrc}); min-height: 500px;`">
        <div class="mb-16">
          <h2 class="text-4xl uppercase font-bold mb-4">{{ getActiveTabContent.title}}</h2>
          <p>{{ getActiveTabContent.description }}</p>
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
          description: 'Some description of design'
        },
        {
          imgSrc: Inside,
          title: 'Performance',
          description: 'Some description of performance'
        },
        {
          imgSrc: Inside,
          title: 'Changing',
          description: 'Some description of tab 3'
        },
        {
          imgSrc: Inside,
          title: 'Comfort',
          description: 'Some description of tab 4'
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