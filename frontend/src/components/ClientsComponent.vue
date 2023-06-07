<template>
  <div class="clients-component">
    <div class="notification">
      <PopUpNotif v-if="showNotif" :textOfNotif="notifMessage" @close-notif="closeNotification"/>
    </div>
    <div class="addition-window">
      <ClientsAdd v-if="showAddWindow" @cancel-window="closeAddWindow"/>
    </div>
    <div class="table-tool-bar-div">
      <TableToolBar class="table-tool-bar" @open-add-window="openAddWindow"/>
    </div>
    <table class="clients-component__table table">
      <tr>
        <th class="clients-component__table-cell table-cell">ФИО</th>
        <th class="clients-component__table-cell table-cell">А/М</th>
        <th class="clients-component__table-cell table-cell">Количество посещений</th>
        <th class="clients-component__table-cell table-cell">Дата последнего посещения</th>
      </tr>
      <tr v-for="client in clients" :key="client.id">
        <td class="clients-component__table-cell table-cell">{{ client.name }}</td>
        <td class="clients-component__table-cell table-cell">{{ client.car }}</td>
        <td class="clients-component__table-cell table-cell">{{ client.visitCount }}</td>
        <td class="clients-component__table-cell table-cell">{{ client.lastVisitDate }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import TableToolBar from '@/components/TableToolBar.vue';
import ClientsAdd from '@/components/ClientsAdd.vue';
import PopUpNotif from './PopUpNotif.vue';

export default {
  name: 'ClientsComponent',
  components: {
    TableToolBar,
    ClientsAdd,
    PopUpNotif,
  },
  data(){
    return {
      clients: [{id: 1, name: 'Жмых Жмыхов Жмыхович', car: 'Митсубиси Лансер', visitCount: 54, lastVisitDate: '25.04.2023'},
      {id: 2, name: 'Жмых Жмыхов Жмыхович', car: 'Митсубиси Лансер', visitCount: 54, lastVisitDate: '25.04.2023'},
      {id: 3, name: 'Жмых Жмыхов Жмыхович', car: 'Митсубиси Лансер', visitCount: 54, lastVisitDate: '25.04.2023'},
      {id: 4, name: 'Жмых Жмыхов Жмыхович', car: 'Митсубиси Лансер', visitCount: 54, lastVisitDate: '25.04.2023'},
      {id: 5, name: 'Жмых Жмыхов Жмыхович', car: 'Митсубиси Лансер', visitCount: 54, lastVisitDate: '25.04.2023'}],
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
.clients-component__table {
  margin: 3rem auto;
}

.clients-component__table-cell {
  width: 15rem;
}

.clients-component__search {
  width: 13rem;
  height: 1.6rem; 
  margin-top: 1rem;
  margin-left: auto;
  margin-right: 3rem;
}

.clients-component__search-field {
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
