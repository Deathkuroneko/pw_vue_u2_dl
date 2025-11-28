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
      <li
        v-show="nombre !== null"
        v-for="{ nombre, apellido } in arreglo"
        :key="nombre"
      >
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