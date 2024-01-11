<template>
  <div>
    <h1>Lista Tareas</h1>
    <input v-model="tarea" type="text" placeholder="Tarea" />
    <button @click="agregarTarea">Añadir</button>
  </div>
</template>

<script>
export default {
  name: "ListaTareas",
  data() {
    return {
      tareas: Array(),
      tarea: "",
    };
  },
  methods: {
    agregarTarea() {
      this.tareas.push(this.tarea),
        console.log("Tareas realizadas:", this.tareas);
    },
  },
};
</script>

<style>
</style>