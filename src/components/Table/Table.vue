<template>
  <div>
    <table>
      <tr>
        <TableHeader v-for="i in inspectionInfo" v-bind:key="i.id"
                     v-bind:inspectionInfo="i"/>
      </tr>
      <tr v-for="i in copyArr"
          v-bind:key="i._id.$oid">
        <TableElem v-for="j in infoKeys" v-bind:key="i._id.$oid + j"
                   v-bind:content="i[j]"
                   v-bind:inspectionInfo="inspectionInfo[j].visibility"/>
      </tr>
    </table>
  </div>
</template>

<script>
import TableElem from "@/components/Table/TableElem";
import TableHeader from "@/components/Table/TableHeader";
export default {
  components: {TableHeader, TableElem},
  component() {
  },
  props: ['info', 'inspectionInfo', 'copyArr', 'infoKeys'],
name: "Table",
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
