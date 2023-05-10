<template>
  <div class="warehose-component">
    <div class="warehose-component__search">
      <input class="warehose-component__search-field input-field" type="text" :value="searchValue" @focusin="clearSearchField" @focusout="findClientByMean">
    </div>
    <table class="warehose-component__table table">
      <tr>
        <th class="warehose-component__table-cell table-cell">Имя справочника</th>
        <th class="warehose-component__table-cell table-cell">Кол-во записей</th>
      </tr>
      <tr v-for="guid in guids" :key="guid.id">
        <td class="warehose-component__table-cell table-cell">{{ guid.name }}</td>
        <td class="warehose-component__table-cell table-cell">{{ guid.count }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'GuidComponent',
  props: {
  },
  data(){
    return {
      guids:[{id: 1, name: 'Марки машин', count: '16'},
      {id: 2, name: 'Марки машин', count: '16'},
      {id: 3, name: 'Марки машин', count: '16'},
      {id: 4, name: 'Марки машин', count: '16'},
      {id: 5, name: 'Марки машин', count: '16'},
      {id: 6, name: 'Марки машин', count: '16'}],
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
.warehose-component__table {
  margin: 3rem auto;
}

.warehose-component__table-cell {
  width: 30rem;
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
</style>
