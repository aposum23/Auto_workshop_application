<template>
  <div class="workers-component">
    <div class="table-tool-bar-div">
      <TableToolBar class="table-tool-bar"/>
    </div>
    <table class="workers-component__table table">
      <tr>
        <th class="workers-component__table-cell table-cell">Имя работника</th>
        <th class="workers-component__table-cell table-cell">Специальность</th>
        <th class="workers-component__table-cell table-cell">Дата приема</th>
        <th class="workers-component__table-cell table-cell">Дата отпуска</th>
      </tr>
      <tr v-for="worker in workers" :key="worker.id">
        <td class="workers-component__table-cell table-cell">{{ worker.name }}</td>
        <td class="workers-component__table-cell table-cell">{{ worker.speciality }}</td>
        <td class="workers-component__table-cell table-cell">{{ worker.admissionDate }}</td>
        <td class="workers-component__table-cell table-cell">{{ worker.vacationDate }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import TableToolBar from '@/components/TableToolBar.vue';

export default {
  name: 'WorkersComponent',
  components: {
    TableToolBar,
  },
  data(){
    return {
      workers: [{id: 1, name: 'Жмых Жмыхов Жмыхович', speciality: '500', vacationDate: '25.04.2023', admissionDate: '25.04.2023'},
      {id: 2, name: 'Жмых Жмыхов Жмыхович', speciality: '500', vacationDate: '25.04.2023', admissionDate: '25.04.2023'},
      {id: 3, name: 'Жмых Жмыхов Жмыхович', speciality: '500', vacationDate: '25.04.2023', admissionDate: '25.04.2023'},
      {id: 4, name: 'Жмых Жмыхов Жмыхович', speciality: '500', vacationDate: '25.04.2023', admissionDate: '25.04.2023'},
      {id: 5, name: 'Жмых Жмыхов Жмыхович', speciality: '500', vacationDate: '25.04.2023', admissionDate: '25.04.2023'}],
      searchValue: 'Поиск',
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
    }
  }
}
</script>

<style scoped>
.workers-component__table {
  margin: 3rem auto;
}

.workers-component__table-cell {
  width: 15rem;
}

.workers-component__search {
  width: 13rem;
  height: 1.6rem; 
  margin-top: 1rem;
  margin-left: auto;
  margin-right: 3rem;
}

.workers-component__search-field {
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
</style>
