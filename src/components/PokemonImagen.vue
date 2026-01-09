<template>
    <div class="pokemon-container"> 
        <img :src="srcImagen" 
        alt="No se puede renderizar" />       
    </div>
</template>
    
<script>
import { consumirAPIFacade } from '../clients/PokemonClient.js';
export default {
    
    props: {
        pokemonId: {
            type: Number,
            required: true
        }
    },     
    computed: {
        // dentro del backticks (``) se usa ${} para insertar variables y vale llamar cualquier logica de js
        srcImagen() {
            return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`;
        }
    }  
}
</script>

<style scoped>

    img {
        position: relative;
        height: 200px;
        right: -42%;
    }   
    .pokemon-container {
        height: 200px;
    }   


</style>