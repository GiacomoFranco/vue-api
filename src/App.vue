<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <!-- <component :is="componenteVariable">
    <h2 v-if="showContent" >Contenido especial</h2>
  </component> -->
  <ComponentRef ref="TemplateElement" someattrs="idkwtf" anotherone="lol"/>
  <div ref="DOMElement">
    <h1>Just a normal div</h1>
    <p>With some text right here</p>
  </div>
  <h2>{{ probandoProvideInject }}</h2>
  <input type="text" ref="specialInput">
</template>

<script>
import { defineAsyncComponent } from 'vue';
const HelloWorld = defineAsyncComponent(() => import('./components/HelloWorld.vue'))
import NuevoComponente from './components/NuevoComponente.vue'
import ComponentRef from './components/ComponentRef.vue';

export default {
  name: 'App',
  components: {
    ComponenteImportado: HelloWorld,
    OtroComponenteImportado: NuevoComponente,
    ComponentRef: ComponentRef
  },
  data(){
    return{
      showContent: false,
      componenteVariable: "ComponenteImportado",
      accesGlobalData: 'Estoy accediendo a esta variable pq es global',
      probandoProvideInject: 'Este es un texto desde provide en el padre y se inyecta en los hijos'
    }
  },
  provide(){
    return{
      textToProvide: this.probandoProvideInject,
      // noExiste: computed(() => this.componenteVariable) 
      // Esta forma de hacer que el provide/inject sea reactiva entra en conflicto y se resuelve en la versión 3.3 de vue, por lo que hay que cambiar una configuración (que no se donde jeje), de esta forma app.config.unwrapInjectedRef = true
    }
  },
  /* LA FORMA EN LA QUE HACEMOS REACTIVA PROVIDE ES VOLVIENDOLA UNA FUNCIÓN QUE RETORNA UN JSON, NO UN OBJETO JSON DE POR SI*/
  mounted(){
    console.log(this.$refs.TemplateElement);
    console.log(this.$refs.DOMElement);
    this.$refs.specialInput.focus()
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
