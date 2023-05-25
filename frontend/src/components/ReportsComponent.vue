<template>
  <div class="users-component">
    <div class="users-component__search">
      <input class="users-component__search-field input-field" type="text" :value="searchValue" @focusin="clearSearchField" @focusout="findClientByMean">
    </div>
    <table class="users-component__table table">
      <tr>
        <th class="users-component__table-cell table-cell">Наименование отчета</th>
        <th class="users-component__table-cell table-cell">Прикреплен к разделам</th>
      </tr>
      <tr v-for="user in users" :key="user.id">
        <td class="users-component__table-cell table-cell">{{ user.name }}</td>
        <td class="users-component__table-cell table-cell">{{ user.attachedChapters }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'UsersComponent',
  props: {
  },
  data(){
    return {
      users: [{id: 1, name: 'Какой-то отчет', attachedChapters: 'Заказы, Клиенты'},
      {id: 2, name: 'Какой-то отчет', attachedChapters: 'Заказы, Клиенты'},
      {id: 3, name: 'Какой-то отчет', attachedChapters: 'Заказы, Клиенты'},
      {id: 4, name: 'Какой-то отчет', attachedChapters: 'Заказы, Клиенты'},
      {id: 5, name: 'Какой-то отчет', attachedChapters: 'Заказы, Клиенты'}],
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
.users-component__table {
  margin: 3rem auto;
}

.users-component__table-cell {
  width: 15rem;
}

.users-component__search {
  width: 13rem;
  height: 1.6rem; 
  margin-top: 1rem;
  margin-left: auto;
  margin-right: 3rem;
}

.users-component__search-field {
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
</style>
