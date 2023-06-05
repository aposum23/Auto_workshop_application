<template>
  <div class="suppliers-component">
    <div class="table-tool-bar-div">
      <TableToolBar class="table-tool-bar"/>
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

export default {
  name: 'SuppliersComponent',
  components: {
    TableToolBar,
  },
  data(){
    return {
      suppliers: [{id: 1, supplierName: 'Жмых Жмыхов Жмыхович', address: 'Ставрополь, Ленина 51', productionType: '25.04.2023'},
      {id: 2, supplierName: 'Жмых Жмыхов Жмыхович', address: 'Ставрополь, Ленина 51', productionType: '25.04.2023'},
      {id: 3, supplierName: 'Жмых Жмыхов Жмыхович', address: 'Ставрополь, Ленина 51', productionType: '25.04.2023'},
      {id: 4, supplierName: 'Жмых Жмыхов Жмыхович', address: 'Ставрополь, Ленина 51', productionType: '25.04.2023'},
      {id: 5, supplierName: 'Жмых Жмыхов Жмыхович', address: 'Ставрополь, Ленина 51', productionType: '25.04.2023'}],
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
</style>
