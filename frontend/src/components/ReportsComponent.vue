<template>
  <div class="reports-component">
    <div class="notification">
      <PopUpNotif v-if="showNotif" :textOfNotif="notifMessage" @close-notif="closeNotification"/>
    </div>
    <div class="addition-window">
      <ReportsAdd v-if="showAddWindow" @cancel-window="closeAddWindow"/>
    </div>
    <div class="reports-component__back-arrow" @click="goBack()">
      <img src="@/assets/backArrow.svg"/>
      <p>Назад</p>
    </div>
    <div class="table-tool-bar-div">
      <TableToolBar class="table-tool-bar" @open-add-window="openAddWindow"/>
    </div>
    <table class="reports-component__table table">
      <tr>
        <th class="reports-component__table-cell table-cell">Наименование отчета</th>
        <th class="reports-component__table-cell table-cell">Прикреплен к разделам</th>
      </tr>
      <tr v-for="report in reports" :key="report.id">
        <td class="reports-component__table-cell table-cell">{{ report.name }}</td>
        <td class="reports-component__table-cell table-cell">{{ report.attachedChapters }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import TableToolBar from '@/components/TableToolBar.vue';
import ReportsAdd from '@/components/ReportsAdd.vue';
import PopUpNotif from './PopUpNotif.vue';

export default {
  name: 'ReportsComponent',
  components: {
    TableToolBar,
    ReportsAdd,
    PopUpNotif,
  },
  data(){
    return {
      reports: [{id: 1, name: 'Какой-то отчет', attachedChapters: 'Заказы, Клиенты'},
      {id: 2, name: 'Какой-то отчет', attachedChapters: 'Заказы, Клиенты'},
      {id: 3, name: 'Какой-то отчет', attachedChapters: 'Заказы, Клиенты'},
      {id: 4, name: 'Какой-то отчет', attachedChapters: 'Заказы, Клиенты'},
      {id: 5, name: 'Какой-то отчет', attachedChapters: 'Заказы, Клиенты'}],
      searchValue: 'Поиск',
      showAddWindow: false,
      showNotif: false,
      notifMessage: '',
    }
  },
  methods:{
    clearSearchField(){
      this.searchValue = '';
    },

    findClientByMean(){
      if (this.searchValue === ''){
        this.searchValue = 'Поиск';
      }
    },

    goBack(){
      let data = {}
      
      data.chapterHeader = 'Администрирование';
      data.chapterType = 'administration';

      this.$emit('change-chapter', data)
    },

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
.reports-component__table {
  margin: 3rem auto;
}

.reports-component__table-cell {
  width: 15rem;
}

.reports-component__search {
  width: 13rem;
  height: 1.6rem; 
  margin-top: 1rem;
  margin-left: auto;
  margin-right: 3rem;
}

.reports-component__back-arrow {
  display: inline-flex;
}

.reports-component__back-arrow:hover {
  cursor: pointer;
}

.reports-component__back-arrow img {
  width: 2rem;
  margin: 1rem;
}

.reports-component__back-arrow p {
  margin: auto;
  font-weight: bold;
  size: 14px;
}

.reports-component__search-field {
  height: 1.5rem;
  width: 10rem;
  padding: 1px;
  padding-right: 1.6rem;
  display: flexbox;
  flex-wrap: wrap;
  background-image: url(../assets/Search.svg);   
  background-repeat: no-repeat;  
  background-position: 10.4rem; 
  background-size: .9rem;
  background-position-y: center;
  outline: none;
}

.table-tool-bar-div {
  margin-top: 2rem;
  text-align: center;
}

.addition-window {
  align: center;
}
</style>
