<template>
  <div class="users-component">
    <div class="users-component__search">
      <input class="users-component__search-field input-field" type="text" :value="searchValue" @focusin="clearSearchField" @focusout="findClientByMean">
    </div>
    <table class="users-component__table table">
      <tr>
        <th class="users-component__table-cell table-cell">Номер</th>
        <th class="users-component__table-cell table-cell">ФИО</th>
        <th class="users-component__table-cell table-cell">Почта</th>
        <th class="users-component__table-cell table-cell">Номер телефона</th>
        <th class="users-component__table-cell table-cell">Роль</th>
      </tr>
      <tr v-for="user in users" :key="user.id">
        <td class="users-component__table-cell table-cell">{{ user.id }}</td>
        <td class="users-component__table-cell table-cell">{{ user.name }}</td>
        <td class="users-component__table-cell table-cell">{{ user.email }}</td>
        <td class="users-component__table-cell table-cell">{{ user.phoneNumber }}</td>
        <td class="users-component__table-cell table-cell">{{ user.role }}</td>
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
      users: [{id: 1, name: 'Жмых Жмыхов Жмыхович', email: 'gmih@mail.ru', phoneNumber: '8(800)555-35-35', role: 'Мастер'},
      {id: 2, name: 'Жмых Жмыхов Жмыхович', email: 'gmih@mail.ru', phoneNumber: '8(800)555-35-35', role: 'Мастер'},
      {id: 3, name: 'Жмых Жмыхов Жмыхович', email: 'gmih@mail.ru', phoneNumber: '8(800)555-35-35', role: 'Мастер'},
      {id: 4, name: 'Жмых Жмыхов Жмыхович', email: 'gmih@mail.ru', phoneNumber: '8(800)555-35-35', role: 'Мастер'},
      {id: 5, name: 'Жмых Жмыхов Жмыхович', email: 'gmih@mail.ru', phoneNumber: '8(800)555-35-35', role: 'Мастер'}],
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
