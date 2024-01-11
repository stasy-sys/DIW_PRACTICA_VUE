<template>
  <div>
    <h1>Lista Tareas</h1>
    <input v-model="tarea" type="text" placeholder="Tarea" />
    <button @click="agregarTarea">Añadir</button>
    <p>Total tareas: {{ totalTareas }}</p>
    <h5>Tareas</h5>
    <li v-for="(tarea, index) in tareas" :key="index">{{ index + 1 }} . {{ tarea }}
        <button @click="eliminarTarea(index)">Eliminar</button>
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
      totalTareas: 0
    };
  },
  methods: {
    agregarTarea() {
      this.tareas.push(this.tarea);
      this.totalTareas = this.tareas.length;
    },
    eliminarTarea(index) {
        this.tareas.splice(index, 1)
    }
  },
};
</script>

<style>
</style>