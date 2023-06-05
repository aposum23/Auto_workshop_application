<template>
  <div class="orders-component">
    <div class="table-tool-bar-div">
      <TableToolBar class="table-tool-bar"/>
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
import TableToolBar from '@/components/TableToolBar.vue';

export default {
  name: 'OrdersComponent',
  components: {
    TableToolBar,
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

.table-tool-bar-div {
  margin-top: 2rem;
  text-align: center;
}
</style>
