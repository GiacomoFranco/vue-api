<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <component :is="componenteVariable">
    <h2>Contenido especial</h2>
  </component>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import NuevoComponente from './components/NuevoComponente.vue'

export default {
  name: 'App',
  components: {
    ComponenteImportado: HelloWorld,
    OtroComponenteImportado: NuevoComponente
  },
  data(){
    return{
      componenteVariable: "OtroComponenteImportado"
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
