<template>
  <div class="warehose-component">
    <div class="notification">
      <PopUpNotif v-if="showNotif" :textOfNotif="notifMessage" @close-notif="closeNotification"/>
    </div>
    <div class="addition-window">
      <WarehouseAdd v-if="showAddWindow" @cancel-window="closeAddWindow"/>
    </div>
    <div class="table-tool-bar-div">
      <TableToolBar class="table-tool-bar" @open-add-window="openAddWindow"/>
    </div>
    <table class="warehose-component__table table">
      <tr>
        <th class="warehose-component__table-cell table-cell">Номер номенклатуры</th>
        <th class="warehose-component__table-cell table-cell">Наименование</th>
        <th class="warehose-component__table-cell table-cell">Остаток</th>
        <th class="warehose-component__table-cell table-cell">Единица измерения</th>
      </tr>
      <tr v-for="nomenclature in warehose" :key="nomenclature.id">
        <td class="warehose-component__table-cell table-cell">{{ nomenclature.nomenclature_number }}</td>
        <td class="warehose-component__table-cell table-cell">{{ nomenclature.name }}</td>
        <td class="warehose-component__table-cell table-cell">{{ nomenclature.remains }}</td>
        <td class="warehose-component__table-cell table-cell">{{ nomenclature.measure_unit }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import TableToolBar from '@/components/TableToolBar.vue';
import WarehouseAdd from '@/components/WarehouseAdd.vue';
import PopUpNotif from './PopUpNotif.vue';

export default {
  name: 'WarehouseComponent',
  components: {
    TableToolBar,
    WarehouseAdd,
    PopUpNotif,
  },
  data(){
    return {
      warehose: [{id: 1, name: 'Полироль', nomenclature_number: '12340981235', remains: '15', measure_unit: 'шт.'},
      {id: 2, name: 'Полироль', nomenclature_number: '12340981235', remains: '15', measure_unit: 'шт.'},
      {id: 3, name: 'Полироль', nomenclature_number: '12340981235', remains: '15', measure_unit: 'шт.'},
      {id: 4, name: 'Полироль', nomenclature_number: '12340981235', remains: '15', measure_unit: 'шт.'},
      {id: 5, name: 'Полироль', nomenclature_number: '12340981235', remains: '15', measure_unit: 'шт.'}],
      showAddWindow: false,
      showNotif: false,
      notifMessage: '',
    }
  },
  methods:{
    openAddWindow(){
      this.showAddWindow = !this.showAddWindow;
    },

    closeAddWindow(message){
      this.showAddWindow = !this.showAddWindow;
      this.notifMessage = message;
      this.showNotif = true;
    },

    closeNotification(){
      this.showNotif = !this.showNotif;
    }
  }
}
</script>

<style scoped>
.warehose-component__table {
  margin: 3rem auto;
}

.warehose-component__table-cell {
  width: 15rem;
}

.warehose-component__search {
  width: 13rem;
  height: 1.6rem; 
  margin-top: 1rem;
  margin-left: auto;
  margin-right: 3rem;
}

.warehose-component__search-field {
  height: 1.5rem;
  width: 10rem;
  padding: 1px;
  padding-right: 1.6rem;
  display: flexbox;
  flex-wrap: wrap;
  background-image: url(../assets/Search.svg);   
  background-repeat: no-repeat; /*Убираем повтор изображения*/   
  background-position: 10.4rem; /*Позиционируем*/   
  background-size: .9rem;
  background-position-y: center;
  outline: none; /*убираем стандартную обводку браузера*/ 
}

.table-tool-bar-div {
  margin-top: 2rem;
  text-align: center;
}

.addition-window {
  align: center;
}
</style>
