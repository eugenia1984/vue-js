<template>
  <div class="presentation flex flex-row">
    <div v-for="col, colIndex in content.columns" :key="colIndex" class="flex-1">{{ col }}</div>
  </div>
</template>

<script>
export default {
  props: {
    content: {
      default: () => {},
      type: Object
    }
  },
  setup(props) {
    console.log("props.content: ",props.content)
  }
}
</script>