<template>
  <table v-if="this.copyArr">
    <tr>
      <th>
        <b>Всего элементов: {{this.copyArr.length}}</b>
      </th>
    </tr>
  </table>
</template>

<script>
export default {
name: "Length",
  props: ['copyArr']
}
</script>

<style scoped>
  div{
    border: solid 2px black;
    width: 100%;
  }
  th{
    height: 50px;
  }
  b{
    float: right;
    margin-right: 60px;
  }
</style>
