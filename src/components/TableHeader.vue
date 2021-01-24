<template>
      <th v-if="inspectionInfo.visibility"><strong>{{inspectionInfo.textContent}}</strong></th>
</template>


<script>
export default {
name: "TableHeader",
  props: ['inspectionInfo']
}
</script>

<style scoped>
th,
tr,
td{
  border: solid 1px black;
  margin: 0;
  padding: 0;
}
strong{
  font-size: 24px;
}
</style>
