<template>
  <div id="app">
    <ContadorView/>
    <Contador/>
    <Contador/>
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