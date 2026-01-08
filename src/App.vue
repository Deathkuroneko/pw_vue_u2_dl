<template>
  <div id="app">
     <PokemonView/>

    <!-- <PreguntaView/> -->
    <!-- <DirectivasView/> -->
    <!--
    <ContadorView/>
    <Contador titulo2="Contador UCE" v-bind:inicio="20" :mostrar="true"/>
    <Contador titulo2="Contador PW" :inicio="4" :mostrar="false"/>
    -->
  </div>
</template>
 
<script>
import ContadorView from '../src/views/ContadorView.vue';
import Contador from '../src/components/Contador.vue';
import DirectivasView from '../src/views/DirectivasView.vue';
import PreguntaView from '../src/views/PreguntaView.vue'
import PokemonView from '../src/views/PokemonView.vue';

export default {
  name: 'App',
  components: {
    ContadorView,
    Contador,
    DirectivasView,
    PreguntaView,
    PokemonView,
  },
 
};
</script>
 
<style>
 
</style>