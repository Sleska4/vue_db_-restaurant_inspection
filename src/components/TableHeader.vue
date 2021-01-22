<template>
    <tr>
      <th v-if="inspectionInfo.business_name"><strong>Название организации</strong></th>
      <th v-if="inspectionInfo.business_address"><strong>Адрес организации</strong></th>
      <th v-if="inspectionInfo.business_phone_number"><strong>Номер организации</strong></th>
      <th v-if="inspectionInfo.business_city"><strong>Город</strong></th>
      <th v-if="inspectionInfo.inspection_date"><strong>Дата инспекции</strong></th>
      <th v-if="inspectionInfo.inspection_description"><strong>Статус инспекции</strong></th>
      <th v-if="inspectionInfo.inspection_type">Тип инспекции</th>
    </tr>
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
