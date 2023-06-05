<template>
  <div class="roles-component">
    <div class="roles-component__back-arrow" @click="goBack()">
      <img src="@/assets/backArrow.svg"/>
      <p>Назад</p>
    </div>
    <div class="table-tool-bar-div">
      <TableToolBar class="table-tool-bar"/>
    </div>
    <table class="roles-component__table table">
      <tr>
        <th class="roles-component__table-cell table-cell">Имя роли</th>
        <th class="roles-component__table-cell table-cell">Краткое описание</th>
      </tr>
      <tr v-for="role in roles" :key="role.id">
        <td class="roles-component__table-cell table-cell">{{ role.name }}</td>
        <td class="roles-component__table-cell table-cell">{{ role.description }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import TableToolBar from '@/components/TableToolBar.vue';

export default {
  name: 'RolesComponent',
  components: {
    TableToolBar,
  },
  data(){
    return {
      roles: [{id: 1, name: 'Мастер', description: 'Занимается ремонтом автомобилей'},
      {id: 2, name: 'Мастер', description: 'Занимается ремонтом автомобилей'},
      {id: 3, name: 'Мастер', description: 'Занимается ремонтом автомобилей'},
      {id: 4, name: 'Мастер', description: 'Занимается ремонтом автомобилей'},
      {id: 5, name: 'Мастер', description: 'Занимается ремонтом автомобилей'}],
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
    },

    goBack(){
      let data = {}
      
      data.chapterHeader = 'Администрирование';
      data.chapterType = 'administration';

      this.$emit('change-chapter', data)
    }
  }
}
</script>

<style scoped>
.roles-component__table {
  margin: 3rem auto;
}

.roles-component__table-cell {
  width: 15rem;
}

.roles-component__search {
  width: 13rem;
  height: 1.6rem; 
  margin-top: 1rem;
  margin-left: auto;
  margin-right: 3rem;
}

.roles-component__back-arrow {
  display: inline-flex;
}

.roles-component__back-arrow:hover {
  cursor: pointer;
}

.roles-component__back-arrow img {
  width: 2rem;
  margin: 1rem;
}

.roles-component__back-arrow p {
  margin: auto;
  font-weight: bold;
  size: 14px;
}

.roles-component__search-field {
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
</style>
