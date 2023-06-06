<template>
  <div class="pop-up-notif">
    <img src="@/assets/Close.svg" class="close" @click="closeNotif"/>
    <p>{{ textOfNotif }}</p>
  </div>
</template>

<script>

export default {
  name: 'PopUpNotif',
  props:{
    textOfNotif: String,
  },
  data(){
    return {
    }
  },
  methods:{
    closeNotif(){
      this.$emit('close-notif');
    }
  }
}
</script>

<style scoped>
.pop-up-notif {
  position:fixed;
  bottom: 0;
  right: 0;
  border: 1px solid #42A08F;
  background-color: #3A3A3A;
  color: #fff;
  padding: 2rem;
}

.close {
  position: absolute;
  top: 0;
  right: 0;
  margin: 1rem;
}
</style>
