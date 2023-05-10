<template>
  <div class="orders-component">
    <div class="orders-component__search">
      <input class="orders-component__search-field input-field" type="text" :value="searchValue" @focusin="clearSearchField" @focusout="findClientByMean">
    </div>
    <table class="orders-component__table table">
      <tr>
        <th class="orders-component__table-cell table-cell">Номер заказа</th>
        <th class="orders-component__table-cell table-cell">Сумма заказа, руб.</th>
        <th class="orders-component__table-cell table-cell">ФИО клиента</th>
        <th class="orders-component__table-cell table-cell">Дата заказа</th>
      </tr>
      <tr v-for="order in orders" :key="order.id">
        <td class="orders-component__table-cell table-cell">{{ order.id }}</td>
        <td class="orders-component__table-cell table-cell">{{ order.sum }}</td>
        <td class="orders-component__table-cell table-cell">{{ order.clientName }}</td>
        <td class="orders-component__table-cell table-cell">{{ order.orderDate }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'OrdersComponent',
  props: {
  },
  data(){
    return {
      orders: [{id: 1, clientName: 'Жмых Жмыхов Жмыхович', sum: '500', orderDate: '25.04.2023'},
      {id: 2, clientName: 'Жмых Жмыхов Жмыхович', sum: '500', orderDate: '25.04.2023'},
      {id: 3, clientName: 'Жмых Жмыхов Жмыхович', sum: '500', orderDate: '25.04.2023'},
      {id: 4, clientName: 'Жмых Жмыхов Жмыхович', sum: '500', orderDate: '25.04.2023'},
      {id: 5, clientName: 'Жмых Жмыхов Жмыхович', sum: '500', orderDate: '25.04.2023'}],
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
.orders-component__table {
  margin: 3rem auto;
}

.orders-component__table-cell {
  width: 15rem;
}

.orders-component__search {
  width: 13rem;
  height: 1.6rem; 
  margin-top: 1rem;
  margin-left: auto;
  margin-right: 3rem;
}

.orders-component__search-field {
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
