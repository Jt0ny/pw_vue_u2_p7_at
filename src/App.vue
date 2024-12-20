<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Contador encabezado="Contador Primero"
  :valor="calcular(1, 3)"
  :esVerdad="muestra1"
  :valor2="78"/>
 
  <Contador encabezado="Contador Segundo"
  v-bind:valor="calcular(5, 3)"
  :esVerdad="muestra2"
  />
 
  <button @:click="cambiar()">Cambiar Primero</button>
  <button @:click="cambiar()">Cambiar Segundo</button>
 
  <div v-if="muestra">
    <p>La propiedad muestra es verdadera</p>
  </div>
  <div v-else>
    <p>La propiedad muestra es falsa</p>
  </div>
</template>
 
<script>
import Contador from './components/Contador.vue'
 
export default {
  name: 'App',
  components: {
    Contador
  },
  methods: {
    calcular(a, b) {
      return a + b;
    },
    cambiar(valor){
      if(valor === 1){
        this.muestra1 = !this.muestra1;
      } else {
        this.muestra2 = !this.muestra2;
     
    }
  }
  },
  data() {
    return {
      muestra1: true,
      muestra2: false
    }
  },
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