<template>
  <div class="table-tool-bar">
    <img src="@/assets/AddButton.svg" class="add-button" @click="openAddWindow"/>
    <input class="table-tool-bar__sort-field input-field" type="text" :value="sortValue" @focusin="clearSortField" @focusout="sortByMean">
    <input class="table-tool-bar__filter-field input-field" type="text" :value="filterValue" @focusin="clearFilterField" @focusout="filterByMean">
    <input class="table-tool-bar__search-field input-field" type="text" :value="searchValue" @focusin="clearSearchField" @focusout="findByMean">
  </div>
</template>

<script>
export default {
  name: 'TableToolBar',
  data(){
    return {
      searchValue: 'Поиск',
      filterValue: 'Фильтр',
      sortValue: 'Сортировка'
    }
  },

  methods:{
    clearSearchField(){
      this.searchValue = '';
    },

    findByMean(){
      if (this.searchValue === ''){
        this.searchValue = 'Поиск';
      }
    },

    clearFilterField(){
      this.filterValue = '';
    },

    filterByMean(){
      if (this.filterValue === ''){
        this.filterValue = 'Фильтр';
      }
    },

    clearSortField(){
      this.sortValue = '';
    },

    sortByMean(){
      if (this.sortValue === ''){
        this.sortValue = 'Сортировка';
      }
    },

    openAddWindow(){
      this.$emit('open-add-window');
    }
  }
}
</script>

<style scoped>
.table-tool-bar {
  background-color: #3A3A3A;
  display: inline-flex;
  padding: .5rem 20rem;
  justify-content: center;
}

.table-tool-bar__search-field {
  display: inline;
  margin: auto 2rem;
  height: 1.5rem;
  width: 10rem;
  padding: 1px;
  padding-right: 1.6rem;
  flex-wrap: wrap;
  background-image: url(../assets/Search.svg);   
  background-repeat: no-repeat;  
  background-position: 10.4rem;  
  background-size: .9rem;
  background-position-y: center;
  outline: none; 
}

.table-tool-bar__filter-field, .table-tool-bar__sort-field{
  display: inline;
  margin: auto 2rem;
  height: 1.5rem;
  width: 10rem;
  padding: 1px;
  padding-right: 1.6rem;
  flex-wrap: wrap;
  outline: none; 
}

.add-button {
  cursor: pointer;
}
</style>
