<template>
  <div>
  <input v-on:input="search" type="text" aria-label="search" class="search"></div>
</template>

<script>
export default {
name: "Search",
  props: ['search'],
  methods: {
  }
}
</script>

<style scoped>
.search{
  height: 40px;
  width: 350px;
}
</style>
