<template>
  <div id="app">
    <ContadorView/>
    <Contador titulo2="Contador UCE" v-bind:inicio="20" :mostrar="true"/>
    <Contador titulo2="Contador PW" :inicio="4" :mostrar="false"/>
  </div>
</template>
 
<script>
import ContadorView from '../src/views/ContadorView.vue';
import Contador from '../src/components/Contador.vue';
export default {
  name: 'App',
  components: {
    ContadorView,
    Contador
  }
 
};
</script>
 
<style>
 
</style>