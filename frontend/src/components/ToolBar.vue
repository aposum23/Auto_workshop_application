<template>
  <div class="tool-bar">
    <div class="tool-bar--button" @click="changeChapter('menu')">
      <div>
        <img src="@/assets/Menu.svg"/>
      </div>
    </div>
    <div class="tool-bar--button" @click="changeChapter('tasks')">
      <div>
        <img src="@/assets/Tasks.svg"/>
      </div>
    </div>
    <div class="tool-bar--button" @click="changeChapter('guid')">
      <div>
        <img src="@/assets/Guid.svg"/>
      </div>
    </div>
    <div class="tool-bar--button" @click="changeChapter('clients')">
      <div>
        <img src="@/assets/Clients.svg"/>
      </div>
    </div>
    <div class="tool-bar--button" @click="changeChapter('suppliers')">
      <div>
        <img src="@/assets/Suppliers.svg"/>
      </div>
    </div>
    <div class="tool-bar--button" @click="changeChapter('warehouse')">
      <div>
        <img src="@/assets/Warehouse.svg"/>
      </div>
    </div>
    <div class="tool-bar--button" @click="changeChapter('workers')">
      <div>
        <img src="@/assets/Workers.svg"/>
      </div>
    </div>
    <div class="tool-bar--button" @click="changeChapter('administration')">
      <div>
        <img src="@/assets/Administration.svg"/>
      </div>
    </div>
    <div class="tool-bar--button" @click="changeChapter('settings')">
      <div>
        <img src="@/assets/Settings.svg"/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ToolBar',
  methods: {
    changeChapter(chapterName){
      let data = {}
      switch(chapterName) {
        case 'menu':
          data.chapterHeader = 'Меню';
          data.chapterType = chapterName;
          break;
        case 'tasks':
          data.chapterHeader = 'Заказы';
          data.chapterType = chapterName;
          break;
        case 'guid':
          data.chapterHeader = 'Справочная информация';
          data.chapterType = chapterName;
          break;
        case 'clients':
          data.chapterHeader = 'Клиенты';
          data.chapterType = chapterName;
          break;
        case 'suppliers':
          data.chapterHeader = 'Поставщики';
          data.chapterType = chapterName;
          break;
        case 'warehouse':
          data.chapterHeader = 'Склад';
          data.chapterType = chapterName;
          break;
        case 'workers':
          data.chapterHeader = 'Работники';
          data.chapterType = chapterName;
          break;
        case 'administration':
          data.chapterHeader = 'Администрирование';
          data.chapterType = chapterName;
          break;
        case 'settings':
          data.chapterHeader = 'Настройки';
          data.chapterType = chapterName;
          break;
        default:
          data.chapterHeader = '';
          data.chapterType = '';
          break;
      }
      this.$emit('change-chapter', data)
    }
  }
}
</script>

<style scoped>
.tool-bar{
  width: 4rem;
  text-align: center;
  background-color: #3A3A3A;
  position: fixed;
  height: 100%;
}

.tool-bar--button{
  height: 4.5rem;
  display: flex;
  user-select: none;
}

.tool-bar--button div{
  margin:auto
}

.tool-bar--button:active{
  background-color: #292929;
}
</style>
