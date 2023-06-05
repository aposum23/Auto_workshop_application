<template>
  <div class="application">
    <ToolBar @change-chapter="changeChapter"/>
    <div class="content">
      <div class="content__header">
        <ChapterHeader :chapterName="chapterName"/>
      </div>
      <div class="content__body">
        <ClientsComponent v-if="chapterType === 'clients'"/>
        <OrdersComponent v-if="chapterType === 'tasks'"/>
        <SuppliersComponent v-if="chapterType === 'suppliers'"/>
        <WorkersComponent v-if="chapterType === 'workers'"/>
        <WarehouseComponent v-if="chapterType === 'warehouse'"/>
        <GuidComponent v-if="chapterType === 'guid'"/>
        <AdministrationComponent @change-chapter="changeChapter" v-if="chapterType === 'administration'"/>
        <UsersComponent @change-chapter="changeChapter" v-if="chapterType === 'users'"/>
        <RolesComponent @change-chapter="changeChapter" v-if="chapterType === 'roles'"/>
        <ReportsComponent @change-chapter="changeChapter" v-if="chapterType === 'reports'"/>
      </div>
    </div>
  </div>
</template>

<script>
import ToolBar from './components/ToolBar.vue';
import ChapterHeader from './components/ChapterHeader.vue';
import ClientsComponent from './components/ClientsComponent.vue';
import OrdersComponent from './components/OrdersComponent.vue';
import SuppliersComponent from './components/SuppliersComponent.vue';
import WorkersComponent from './components/WorkersComponent.vue';
import WarehouseComponent from './components/WarehouseComponent.vue';
import GuidComponent from './components/GuidComponent.vue';
import AdministrationComponent from './components/AdministrationComponent.vue';
import UsersComponent from './components/UsersComponent.vue';
import RolesComponent from './components/RolesComponent.vue';
import ReportsComponent from './components/ReportsComponent.vue';

export default {
  name: 'App',
  components: {
    ToolBar,
    ChapterHeader,
    ClientsComponent,
    OrdersComponent,
    SuppliersComponent,
    WorkersComponent,
    WarehouseComponent,
    GuidComponent,
    AdministrationComponent,
    UsersComponent,
    RolesComponent,
    ReportsComponent,
  },
  data(){
    return {
      chapterName: 'Меню',
      chapterType: 'menu',
    }
  },
  methods:{
    changeChapter(data){
      this.chapterName = data.chapterHeader;
      this.chapterType = data.chapterType;
    }
  }
}
</script>

<style>
body {
  margin: 0px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.content {
  margin-left: 4rem;
}

.table-cell {
  border: 1px solid #42A08F;
  padding: 1rem;
}

.table {
  border-collapse: collapse;
}

.input-field {
  border: 1px solid #42A08F;
}
</style>
