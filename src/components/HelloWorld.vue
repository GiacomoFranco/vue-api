<template>
  <div v-if="isMenu">
    <button @click="show = !show">Menu</button>
    <transition name="fade">
      <Menu v-show="show"/>
    </transition>
  </div>
  <Modal/>
</template>

<script>
import Menu from './Menu.vue';
import Modal from './Modal.vue';

export default {
  name: 'HelloWorld',
  components: {
    Menu,
    Modal
},
  data() {
    return {
      show: false,
      isMenu: true,
    }
  },
  beforeCreate(){
    console.log('beforeCreate',this.$data,this.$el);
  },
  created(){
    console.log('created',this.$data,this.$el);
  },
  beforeMount(){
    console.log('beforeMount',this.$data,this.$el);
  },
  mounted(){
    console.log('mounted',this.$data,this.$el);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}

button {
  background-color: #42b983;
  color: white;
  border: none;
  height: 50px;
  width: 150px;
  border-radius: 50px;
  cursor: pointer;
  margin: 50px;
}

a {
  color: #42b983;
}


.fade-enter-from,
.fade-leave-to{
  opacity: 0;
}

.fade-leave-active,
.fade-enter-active {
  transition: opacity 0.5s ease;
}

</style>
