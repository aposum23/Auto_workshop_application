<template>
  <div class="roles-component">
    <div class="notification">
      <PopUpNotif v-if="showNotif" :textOfNotif="notifMessage" @close-notif="closeNotification"/>
    </div>
    <div class="addition-window">
      <RolesAdd v-if="showAddWindow" @cancel-window="closeAddWindow"/>
    </div>
    <div class="roles-component__back-arrow" @click="goBack()">
      <img src="@/assets/backArrow.svg"/>
      <p>Назад</p>
    </div>
    <div class="table-tool-bar-div">
      <TableToolBar class="table-tool-bar" @open-add-window="openAddWindow"/>
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
import RolesAdd from '@/components/RolesAdd.vue';
import PopUpNotif from './PopUpNotif.vue';

export default {
  name: 'RolesComponent',
  components: {
    TableToolBar,
    RolesAdd,
    PopUpNotif,
  },
  data(){
    return {
      roles: [{id: 1, name: 'Мастер', description: 'Занимается ремонтом автомобилей'},
      {id: 2, name: 'Мастер', description: 'Занимается ремонтом автомобилей'},
      {id: 3, name: 'Мастер', description: 'Занимается ремонтом автомобилей'},
      {id: 4, name: 'Мастер', description: 'Занимается ремонтом автомобилей'},
      {id: 5, name: 'Мастер', description: 'Занимается ремонтом автомобилей'}],
      showAddWindow: false,
      showNotif: false,
      notifMessage: '',
    }
  },
  methods:{
    goBack(){
      let data = {}
      
      data.chapterHeader = 'Администрирование';
      data.chapterType = 'administration';

      this.$emit('change-chapter', data)
    },

    openAddWindow(){
      this.showAddWindow = !this.showAddWindow;
    },

    closeAddWindow(message){
      this.showAddWindow = !this.showAddWindow;
      this.notifMessage = message;
      this.showNotif = true;
    },

    closeNotification(){
      this.showNotif = !this.showNotif;
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
