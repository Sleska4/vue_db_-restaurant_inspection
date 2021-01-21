<template>
  <table>
    <tr v-for="i in copyArr" v-bind:key="i._id.$oid">
      <th v-if="inspectionInfo.business_name">{{i.business_name}}</th>
      <th v-if="inspectionInfo.business_address">{{i.business_address}}</th>
      <th v-if="inspectionInfo.business_phone_number">{{i.business_phone_number}}</th>
      <th v-if="inspectionInfo.business_city">{{i.business_city}}</th>
      <th v-if="inspectionInfo.inspection_date">{{i.inspection_date}}</th>
      <th v-if="inspectionInfo.inspection_description">{{i.inspection_description}}</th>
      <th v-if="inspectionInfo.inspection_type">{{i.inspection_type}}</th>
    </tr>
  </table>
</template>

<script>
export default {
props: ['info', 'inspectionInfo', 'copyArr'],
name: "Table",
methods: {
},
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
</style>
