<template>
  <th v-if="inspectionInfo">{{content}}</th>
</template>

<script>
export default {
name: "TableElem",
  props: ['content', 'inspectionInfo'],
  methods:{
  }
}
</script>

<style scoped>

</style>
