<template>
  <div v-on:click="inspectionInfo[elem] = !inspectionInfo[elem]">
    <span class="elem" v-if="this.inspectionInfo[elem]">✔</span>
    <span class="elem" v-else>✘</span>
    <span>{{this.text}}</span>
  </div>
</template>

<script>
export default {
name: "MenuElements",
  props:['elem', 'inspectionInfo', 'text']
}
</script>

<style scoped>

</style>
