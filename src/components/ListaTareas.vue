<template>
  <div>
    <h1>Lista Tareas</h1>
    <input v-model="tarea" type="text" placeholder="Tarea" />
    <button @click="agregarTarea">Añadir</button>
    <li v-for="item in tareas" :key="item">
      {{ item }}
    </li>
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
      this.tareas.push(this.tarea);
    },
  },
};
</script>

<style>
</style>