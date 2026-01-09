<template>
    <div>
        <PokemonImagen :pokemonId="pokemonGanador" />
        <PokemonOpciones @seleccionado="evaluarGanador($event)" :listaPokemons="pokemonArr"/>
        <div class="resul">
          <p>{{ resultado }}</p>
        </div>
        
    </div>
</template>

<script>
    import PokemonImagen from '@/components/PokemonImagen.vue';
    import PokemonOpciones from '@/components/PokemonOpciones.vue';
    import { obtenerVectorPokemonFacade,obtenerAleatorioFacade } from '../clients/PokemonClient.js';
export default {
  components:{
    PokemonImagen,
    PokemonOpciones,
  },
  data() {
    return {
      pokemonArr: [],
      pokemonGanador: null,
      resultado: '',
    };
  },
  // mounted es un hook del ciclo de vida del componente
  mounted() {
    console.log('Componente montado');
    this.iniciarJuego();
  },
  methods: {
    async iniciarJuego() {
    this.pokemonArr = await obtenerVectorPokemonFacade();

    const numero = obtenerAleatorioFacade(0,3)
    this.pokemonGanador = this.pokemonArr[numero].id;
    console.log('Pokemon ganador:', this.pokemonArr[numero].nombre,  this.pokemonArr[numero].id);

    },
    evaluarGanador(idSeleccionado) {
      console.log('ERecibido del Padre');
      console.log('ID seleccionado:', idSeleccionado);

        if (idSeleccionado === this.pokemonGanador) {
          console.log('¡Correcto! Has seleccionado el Pokémon ganador.');
          // como agrego el nombre del pokemon ganador al mensaje?
            this.resultado = `¡Correcto! Has seleccionado el Pokémon ganador es ¡ ${this.pokemonArr.find(p => p.id === this.pokemonGanador)?.nombre} !` ;
        } else {
          console.log('Incorrecto. Inténtalo de nuevo.');
            this.resultado = `Incorrecto era ${this.pokemonArr.find(p => p.id === this.pokemonGanador)?.nombre}. Inténtalo de nuevo.`;
        }
        this.iniciarJuego();
    },
  },
};

</script>

<style scoped>
h1 {
    color: blue;
}
.resul{
    display: flex;
    justify-content: center;
    margin-top: 20px;
}
p {
    font-size: 20px;
    font-weight: bold;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
</style>