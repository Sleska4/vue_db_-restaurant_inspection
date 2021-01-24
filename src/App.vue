<template>
  <div>
  <table class="menu">
      <tr>
        <th>
          <h1>Инспекция по ресторанам</h1>
        </th>
        <th class="middle-th">
          <div class="position">
          <button class="settings-btn" v-on:click="toggle()">Редактировать таблицу</button>
          <div class="settings" id="menu">
            <MenuElements
                v-for="i in inspectionInfo"
                v-bind:key="i.id"
                v-bind:inspectionInfo="i"
            />
          </div>
          </div>
        </th>
        <th>
          <Search v-bind:search="search" />
        </th>
      </tr>
    </table>
    <Table v-bind:info="info"
           v-bind:inspectionInfo="inspectionInfo"
           v-bind:copyArr="copyArr"
           v-bind:infoKeys="Object.keys(inspectionInfo)"
      />
    <Length v-bind:copyArr="copyArr"/>
  </div>
</template>

<script>
import data from './json.json'
import Table from "@/components/Table/Table";
import Search from "@/components/Search/Search";
import MenuElements from "@/components/Menu/MenuElements";
import Length from "@/components/Length/Length";


export default {
  name: 'App',
  components: {
    Length,
    MenuElements,
    Search,
    Table,
  },
  data (){
    return{
      info: [...data],
      inspectionInfo: {
        'business_name': {
          'visibility': true,
          'textContent': 'Название организации',
          id: 1},

        'business_address': {
          'visibility': true,
          'textContent': 'Адрес организации',
          id: 2},

        'business_phone_number': {
          'visibility': false,
          'textContent': 'Номер организации',
          id: 3},

        'business_city': {
          'visibility': true,
          'textContent': 'Город',
          id: 4},

        'inspection_date': {
          'visibility': true,
          'textContent': 'Дата инспекции',
          id: 5},

        'inspection_description': {
          'visibility': true,
          'textContent': 'Статус инспекции',
          id: 6},

        'inspection_type': {
          'visibility': false,
          'textContent': 'Тип инспекции',
          id: 7}
      },
      copyArr: null,
      menu: false,
    }
  },
  mounted () {
    if(data){
      this.info = [...data];
    } else{
      alert('При загрузки базы данных возникла ошибка. Повторите попытку позже.');
      this.info = [];
    }
    this.copyArr = JSON.parse(JSON.stringify(this.info));
  },
  methods: {
    search(e){
      if(e.target.value.length === 0){
        this.copyArr = this.info;
        return
      }
      const res = []
      this.info.forEach(el => {
        const v = Object.values(el).splice(1);
        for(let i of v) {
          if (i.search(e.target.value) > -1){
            res.push(el);
            break
          }
        }
        this.copyArr = res;
      })
    },
    toggle(){
      this.menu = !this.menu;
      const menu = document.querySelector('#menu');
      if(this.menu){
        menu.classList.add('visible');
      }else {
        menu.classList.remove('visible');
      }
    }
  }
}
</script>

<style>
table{
  border: 1px solid black;
  width: 100%;
}
.settings-btn{
  width: 100%;
  height: 100%;
}
.settings{
  display: none;
  position: absolute;
  left: 0;
  top: 63px;
  background-color: white;
  width: 250px;
}
.position{
  width: 250px;
  height: 40px;
  background-color: gray;
  position: relative;
}
.settings.visible{
  display: block;
}
</style>
