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


/*    search(e){
if(e.target.value.length === 0){
this.copyArr = this.info;
return
}
const res = []
this.copyArr.forEach(el => {        //Перебирает объект
const v = Object.values(el).splice(1);
for(let i of v) {
if (i.search(e.target.value) > -1){
res.push(el);
break
}
}
this.copyArr = res;
})
}*/
