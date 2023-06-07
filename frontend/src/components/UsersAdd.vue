<template>
  <div class="reports-add">
    <div class="input-group">
      <label class="input-group-element">Наименование отчета</label>
      <input class="input-group-element input-field" type="text" :value="nameOfReport" @focusin="clearSortField" @focusout="sortByMean">
    </div>
    <div class="input-group">
      <label class="input-group-element">Объекты отчета</label>
      <input class="input-group-element input-field" type="text" :value="objects" @focusin="clearSortField" @focusout="sortByMean">
    </div>
    <div class="input-group">
      <label class="input-group-element">Файл отчета</label>
      <input class="input-group-element input-field" type="file" :value="fileOfReport" @focusin="clearSortField" @focusout="sortByMean">
    </div>
    <div class="input-group">
      <label class="input-group-element">Краткое описание</label>
      <input class="input-group-element input-field description" type="text" :value="shortDescription" @focusin="clearSortField" @focusout="sortByMean">
    </div>
    <div class="button-block">
      <input type="button" value="Отменить" class="button" @click="cancelWindow('Изменения отменены')"/>
      <input type="button" value="Применить" class="button" @click="addNewRecord"/>
    </div>
  </div>
</template>

<script>

export default {
  name: 'UsersAdd',
  props:{

  },
  data(){
    return {
      nameOfReport: '',
      objects: '',
      fileOfReport: '',
      shortDescription: '',
    }
  },
  methods:{
    cancelWindow(message){
      this.$emit('cancel-window', message);
    },

    addNewRecord(){
      this.cancelWindow('Изменения приняты');
    }
  }
}
</script>

<style scoped>
.reports-add {
  background-color: #3A3A3A;
  width: 90%;
  height: 80%;
  position: fixed;
  top: 15%;
  left: 7.5%;
  color: #FFFFFF;
}
.input-field {
  display: inline;
  height: 1.5rem;
  width: 10rem;
  padding: 1px;
  padding-right: 1.6rem;
  flex-wrap: wrap;
  outline: none; 
}

.input-group {
  margin: 2rem 2rem;
  display:inline-block;
}

input, label {
  display:block;
}

label {
  margin: 0px;
  padding: 0px;
}

.description {
  width: 80em;
  height: 10em;
}

.button {
  background-color: #3A3A3A;
  border: none;
  color: #FFFFFF;
  cursor: pointer;
  display: inline-block;
  margin: 1rem;
}

.button-block {
  position: absolute;
  right: 0;
  bottom: 0;
}
</style>
