<template>
  <div class="administration-component">
    <div class="administration-component__search">
      <input class="administration-component__search-field input-field" type="text" :value="searchValue" @focusin="clearSearchField" @focusout="findClientByMean">
    </div>
    <div class="administration-chapters">
      <ul>
        <div v-for="chapter in administrationChapters" :key="chapter">
          <li class="chapter"><p @click="changeChapter(chapter)">{{ chapter.label }}</p></li>
        </div>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AdministrationComponent',
  props: {
  },
  data(){
    return {
      administrationChapters: [{label: 'Пользователи', type: 'users'}, {label: 'Роли', type: 'roles'},
       {label: 'Компания', type: 'company'}, {label: 'Отчеты', type: 'reports'},
        {label: 'Расширение тарифа', type: 'tariffExtension'}, {label: 'Помощь', type: 'help'}],
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

    changeChapter(chapter){
      let data = {}
      
      data.chapterHeader = chapter.label;
      data.chapterType = chapter.type;

      this.$emit('change-chapter', data)
    }
  }
}
</script>

<style scoped>
.administration-component__search {
  width: 13rem;
  height: 1.6rem; 
  margin-top: 1rem;
  margin-left: auto;
  margin-right: 3rem;
}

.administration-component__search-field {
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

.administration-chapters {
  margin: 1rem 2rem;
}

.chapter {
  margin: 1rem 0rem;
  user-select: none;
  width: 10rem;
}

.chapter:active {
  color: #42A08F;
}

.chapter:hover {
  color: #928e8e;
  cursor: pointer;
}
</style>
