<template>
  <div v-on:click="inspectionInfo.visibility = !inspectionInfo.visibility">
    <span v-if="this.inspectionInfo.visibility">✔</span>
    <span v-else>✘</span>
    <span>{{inspectionInfo.textContent}}</span>
  </div>
</template>

<script>
export default {
name: "MenuElements",
  props:['inspectionInfo'],

}
</script>

<style scoped>

</style>
