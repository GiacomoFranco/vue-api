<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <component :is="componenteVariable">
    <h2 v-if="showContent" >Contenido especial</h2>
  </component>
</template>

<script>
import { defineAsyncComponent } from 'vue';

const HelloWorld = defineAsyncComponent(() => import('./components/HelloWorld.vue'))
import NuevoComponente from './components/NuevoComponente.vue'

export default {
  name: 'App',
  components: {
    ComponenteImportado: HelloWorld,
    OtroComponenteImportado: NuevoComponente
  },
  data(){
    return{
      showContent: false,
      componenteVariable: "ComponenteImportado",
    }
  }
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

[alt="Vue logo"]{
  width: 200px;
  height: 200px;
}

</style>
