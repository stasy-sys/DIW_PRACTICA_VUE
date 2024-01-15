<template>
  <div>
    <h1>Lista Tareas</h1>
    <input v-model="tarea.text" type="text" placeholder="Tarea" />
    <button @click="agregarTarea">Añadir</button>
    <p>Total tareas: {{ totalTareas }}</p>
    <h5>Tareas</h5>
    <li v-for="(texto, index) in tareas" :key="index" :id=index>{{ index + 1 }} . {{ texto }}
        <button @click="eliminarTarea(index)">Eliminar</button>
        <input type="checkbox" @change="marcarComoCompletada(index)"/>
        <p>{{ tarea.fecha }}</p>
    </li>
  </div>
</template>

<script>
export default {
  name: "ListaTareas",
  data() {
    return {
      tareas: Array(),
      tarea: {
        text: "",
        fecha: ""
      },
      totalTareas: 0,
      tareasCompletadas: [],
      fecha: ""
    };
  },
  methods: {
    agregarTarea() {
      this.tarea.fecha = new Date (). toLocaleString();
      let nuevaTarea = this.tarea;
      this.tareas.push(nuevaTarea.text);
      this.totalTareas = this.tareas.length;
      this.guardarTareasEnLocalStorage();
    },
    eliminarTarea(index) {
        this.tareas.splice(index, 1);
    },
    marcarComoCompletada(index) {
      this.tareasCompletadas.push(this.tareas[index]);
      if(document.getElementById(index).getAttribute('class') == 'completada'){
        document.getElementById(index).setAttribute('class', 'normal');
      } else {
        document.getElementById(index).setAttribute('class', 'completada');
      }
    },
    guardarTareasEnLocalStorage() {
      localStorage.setItem('tareas', JSON.stringify(this.tareas));
    }, 
    cargarTareasDesdeLocalStorage() {
      const tareasGuardadas =
      localStorage.getItem('tareas');
      if (tareasGuardadas) {
        this.tareas = JSON.parse(tareasGuardadas);
      }
    }
  },
  mounted() {
    this.cargarTareasDesdeLocalStorage();
  }
};
</script>

<style>
.completada {
  color: red;
}
</style>