<template>
  <div>
  <table class="menu">
      <tr>
        <th>
          <h1>Инспекция по ресторанам</h1>
        </th>
        <th class="middle-th">
          <div class="position">
          <button class="settings-btn" v-on:click="toggle">Редактировать таблицу</button>
          <div class="settings" id="menu">
            <MenuElements
                v-bind:inspectionInfo="inspectionInfo"
                v-bind:elem="'business_name'"
                v-bind:text="'Наименование организации'"/>
            <MenuElements
                v-bind:inspectionInfo="inspectionInfo"
                v-bind:elem="'business_address'"
                v-bind:text="'Адрес организации'"/>
            <MenuElements
                v-bind:inspectionInfo="inspectionInfo"
                v-bind:elem="'business_city'"
                v-bind:text="'Город организации'"/>
            <MenuElements
                v-bind:inspectionInfo="inspectionInfo"
                v-bind:elem="'business_phone_number'"
                v-bind:text="'Номер организации'"/>
            <MenuElements
                v-bind:inspectionInfo="inspectionInfo"
                v-bind:elem="'inspection_date'"
                v-bind:text="'Дата инспекции'"/>
            <MenuElements
                v-bind:inspectionInfo="inspectionInfo"
                v-bind:elem="'inspection_description'"
                v-bind:text="'Статус инспекции'"/>
            <MenuElements
                v-bind:inspectionInfo="inspectionInfo"
                v-bind:elem="'inspection_type'"
                v-bind:text="'Тип инспекции'"/>
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
      />
    <Length v-bind:copyArr="copyArr"/>
  </div>
</template>

<script>
import data from './json.json'
import Table from "@/components/Table";
import Search from "@/components/Search";
import MenuElements from "@/components/MenuElements";
import Length from "@/components/Length";


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
      info: null,
      inspectionInfo: {
        business_name: true,
        business_address: true,
        business_phone_number: false,
        business_city: true,
        inspection_date: true,
        inspection_description: true,
        inspection_type: false
      },
      copyArr: null,
      menu: false,
    }
  },
  mounted () {
    /*fetch('http://localhost:3001/content\n')                 В папке serve отредактированный.
        .then(res => res.json())
        .then(json => {
          this.info = json;
          this.copyArr = JSON.parse(JSON.stringify(this.info))
        });*/

        this.info = data;
        this.copyArr = JSON.parse(JSON.stringify(this.info))
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
