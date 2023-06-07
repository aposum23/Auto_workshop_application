<template>
  <div class="suppliers-component">
    <div class="notification">
      <PopUpNotif v-if="showNotif" :textOfNotif="notifMessage" @close-notif="closeNotification"/>
    </div>
    <div class="addition-window">
      <SuppliersAdd v-if="showAddWindow" @cancel-window="closeAddWindow"/>
    </div>
    <div class="table-tool-bar-div">
      <TableToolBar class="table-tool-bar" @open-add-window="openAddWindow"/>
    </div>
    <table class="suppliers-component__table table">
      <tr>
        <th class="suppliers-component__table-cell table-cell">Наименование поставщика</th>
        <th class="suppliers-component__table-cell table-cell">Адрес нахождения</th>
        <th class="suppliers-component__table-cell table-cell">Тип поставляемой продукции</th>
      </tr>
      <tr v-for="supplier in suppliers" :key="supplier.id">
        <td class="suppliers-component__table-cell table-cell">{{ supplier.supplierName }}</td>
        <td class="suppliers-component__table-cell table-cell">{{ supplier.address }}</td>
        <td class="suppliers-component__table-cell table-cell">{{ supplier.productionType }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import TableToolBar from '@/components/TableToolBar.vue';
import SuppliersAdd from '@/components/SuppliersAdd.vue';
import PopUpNotif from './PopUpNotif.vue';

export default {
  name: 'SuppliersComponent',
  components: {
    TableToolBar,
    SuppliersAdd,
    PopUpNotif,
  },
  data(){
    return {
      suppliers: [{id: 1, supplierName: 'Жмых Жмыхов Жмыхович', address: 'Ставрополь, Ленина 51', productionType: '25.04.2023'},
      {id: 2, supplierName: 'Жмых Жмыхов Жмыхович', address: 'Ставрополь, Ленина 51', productionType: '25.04.2023'},
      {id: 3, supplierName: 'Жмых Жмыхов Жмыхович', address: 'Ставрополь, Ленина 51', productionType: '25.04.2023'},
      {id: 4, supplierName: 'Жмых Жмыхов Жмыхович', address: 'Ставрополь, Ленина 51', productionType: '25.04.2023'},
      {id: 5, supplierName: 'Жмых Жмыхов Жмыхович', address: 'Ставрополь, Ленина 51', productionType: '25.04.2023'}],
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
.suppliers-component__table {
  margin: 3rem auto;
}

.suppliers-component__table-cell {
  width: 15rem;
}

.suppliers-component__search {
  width: 13rem;
  height: 1.6rem; 
  margin-top: 1rem;
  margin-left: auto;
  margin-right: 3rem;
}

.suppliers-component__search-field {
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
