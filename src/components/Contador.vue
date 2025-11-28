<template>
  <div>
    <h1>{{ titulo2 }}</h1>
    <!--Para usar cualquier  codigo de js debemos usar: {{}}-->
    <p>{{ numero }}<sup>2</sup>={{ calculaCuadrado }}</p>
    <p>{{ numero }}<sup>2</sup>={{ calculaCuadrado }}</p>
    <p>{{ numero }}<sup>2</sup>={{ calculaCuadrado }}</p>
    <p>{{ numero }}<sup>3</sup>={{ calculaCubo }}</p>
    <p>{{ numero }}<sup>3</sup>={{ obtenerCubo() }}</p>
    <div id='incrementar'>
      <button class="boton" @:click="incrementar()">+</button>
      <button class="boton" v-on:click="decrementar()">-</button>
      <button v-if="mostrar">Prueba</button>
      <!--v-if no construye el elemento y v-shown oculta el elemento de display-->
    </div>
  </div>
</template>
<!--las directivas son palabras clave que permite a VUE manipular el DOM  de manera ractiva-->
<script>
export default {
  //declaracion de propiedades reactivas - variables a usar dentro de nuestros componente
  //si se cambia algo dentro del js se actualzia reactivamente en la pagina web
  data() {
    return {
      numero: this.inicio,
      titulo: "Contador",
    };
  },
  // para metodos
  methods: {
    // cuando se usa una propiedad reactiva dentro del script lo correcto es usar la palabra reservada this
    obtenerCuadrado() {
      console.log("Entro a obtener cuadrado");
      return this.numero * this.numero;
    },
    obtenerCubo() {
      console.log("Entro a obtener cubo");
      return this.numero * this.numero * this.numero;
    },
    incrementar() {
        console.log(this.titulo2);
      this.numero++;
    },
    decrementar() {
      this.numero--;
    },
  },
  // propiedades computadas - son elementos que se ejecutan solo si cambia el resultado de la ejecucion de su cuerpo
  // jamas puede recibir un argumento
  // siempre guarda su resultado en cache
  computed: {
    calculaCuadrado() {
      console.log("Entro a propiedad computada");
      return this.numero * this.numero;
    },
    calculaCubo() {
      console.log("Entro a propiedad computada");
      return this.numero * this.numero * this.numero;
    },
  },
  //props - son variables a nivel de componente q yo puedo instanciar desde un componente externo a mi componente
  //esa variable puede ser llenada por el padre para q entre como variable al componente
   // props:['titulo2', "inicio", "mostrar"], DECLARACION BASICA
  // lo ideal mandar el v-bin o : si es un numero y se es texto se puede omitir
    props: {
        titulo2: String,
        inicio: {
            type: Number,
            default: 99,
            validator(value){
                return value > 10;
            }
        },
        mostrar: Boolean
    }
    /*string, number, boolean. array, object, date, funcion, BigInt*/
};
</script>

<style>

#incrementar{
    display: flex; 
    justify-content: center; 
}

.boton {
    background: red;
    border: 2px solid aqua;
}

</style>