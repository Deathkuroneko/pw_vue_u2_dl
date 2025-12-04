<template>
  <div>
    <!--Relacionar el imput a un laber o valor
    el v-model es una propiedad reactiva-->
    <label for="id_nombre">Nombre</label>
    <input v-model="nombre" id="id_nombre" type="text" />

    <label for="id_apellido">Apellido</label>
    <input v-model="apellido" id="id_apellido" type="text" />

    <p>Hola mi Lord, {{ nombre + apellido }}</p>
    <h1>{{ arreglo }}</h1>

    <ul>
      <li v-show="nombre !== null" v-for="{ nombre, apellido } in arreglo" :key="nombre">
        {{ nombre }}
        {{ apellido }}
      </li>
    </ul>
    <h2>Tabla</h2>
    <div id="div_tabla">
    <table id="table">
      <tr>
        <th>Nombre</th>
        <th>Apellido</th>
      </tr>
      <!-- Segunda forma llamando directo desde el objeto
      <tr v-for="Estudiante in arreglo" :key="Estudiante">
        <td v-show="nombre !== null">{{ Estudiante.nombre }}</td>
        <td v-show="apellido !== null">{{ Estudiante.apellido }}</td>
      </tr>
      -->
      <tr v-for="{ nombre, apellido } in arreglo" :key="nombre">
        <td class="caja" v-show="nombre !== null">{{ nombre }}</td>
        <td class="caja" v-show="apellido !== null">{{ apellido }}</td>
      </tr>
    </table>
    </div>
    <!--Directiva para iterar sobre una lista (v-for)-->
    <button v-on:click="imprimirNombreApellido()">Imprimir nombre</button>
    <button v-on:click="agregarEstudiante()">Imprimir Estudainte</button>
    <button v-on:click="limpiarFormulario()">Limpiar</button>
    <h1>{{ arreglo }}</h1>
    <hr/>
    <label for="id_nombre_1">Nombre</label>
    <input v-model="nombre" id="id_nombre_1" type="text">
    <label for="id_apellido_1">Apellido</label>
    <!--Los modificadores de eventos modificadores de eventos que existen
    https://vuejs.org/guide/essentials/event-handling.html#key-modifiers -->
    <input v-model="apellido" v-on:keypress.space="agregarEstudiante1" id="id_apellido_1" type="text">
    <ul>
      <li v-show="nombre" v-for="{ nombre, apellido } in arreglo" :key="nombre" >
        {{ nombre }} + {{ apellido }}
      </li>
    </ul>
    <h2>Tabla</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nombre: null,
      apellido: null,
      arreglo: [],
    };
  },
  methods: {
    imprimirNombreApellido() {
      console.log(this.nombre), console.log(this.apellido);
    },
    agregarEstudiante() {
      const stu = {
        nombre: this.nombre,
        apellido: this.apellido,
      };
      console.log("Agregar estudiante");
      console.log(stu);
      this.arreglo.push(stu);
    },
    agregarEstudiante1(event) {
      console.log('ahora');
      const stu = {
        nombre: this.nombre,
        apellido: this.apellido,
      };
      if(event.charCode !== 32 ){
        return;
      }
      console.log("Agregar estudiante");
      console.log(stu);
      this.arreglo.push(stu);
    },
    limpiarFormulario() {
      this.nombre = null;
      this.apellido = null;
    },
  },
};
</script>

<style>
#div_tabla{
    display: flex;
    justify-content: center;
}
#table{
    border: 2px solid black;
}
.caja{
    border: 2px solid red;
}
</style>