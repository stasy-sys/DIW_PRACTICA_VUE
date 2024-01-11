<template>
    <div class="hello">
        <h3>{{ mensaje }}</h3>
        <h5>Listado de Items:</h5>
        <ul>
            <li v-for="item in listaItems" :key="item.id">
                {{ item.nombre }}--{{ item.apellido }}
            </li>
        </ul>
        <h5>Nombre del cliente: {{ nombreCliente }}</h5>
        <h5>Contador: {{ contador }}</h5>
        <button @click='incrementar'> Incrementar</button>
        <br>
        <hr>
        <div>
            <input v-model="numero1" type="text" placeholder="Número 1">
            <input v-model="numero2" type="text" placeholder="Número 2">
            <button @click='sumar'> Sumar</button>
            <button @click='restar'> Resta</button>
            <h5>Resultado de la suma: {{ resultadoSuma }}</h5>
            <p v-if="resultadoSuma > 0">La suma es mayor que 0</p>
            <p v-else> La suma es menor que 0</p>
            <h5>Resultado de la resta: {{ resultadoResta }}</h5>
            <p v-if="resultadoResta > 0">La resta es mayor que 0</p>
            <p v-else> La resta es menor que 0</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'PrimerasPruebas',
    props: {
        mensaje: String,
        nombre: {
            type: String,
            default: 'Pepe'
        }, 
        apellidos: {
            type: String,
            default: 'Perez'
        }
    },
    computed: {
        nombreCliente() {
            return this.nombre + ' ' + this.apellidos;
        }
    },
    watch: {
        contador(nuevoMensaje, viejoMensaje) {
            console.log(`Hemos pasado de " ${viejoMensaje} " a " ${nuevoMensaje} "`);
        }
    },
    methods: {
        incrementar() {
            this.contador++;
        },
         sumar() {
            const num1 = parseFloat(this.numero1);
            const num2 = parseFloat(this.numero2);
            //comprueba si son números
            if (isNaN(num1) && isNaN(num2)) {
                alert('No son números');
            } else {
                this.resultadoSuma = num1 + num2;
            }
         },
         restar() {
            const num1 = parseFloat(this.numero1);
            const num2 = parseFloat(this.numero2);
            //comprueba si son números
            if (isNaN(num1) && isNaN(num2)) {
                alert('No son números');
            } else {
                this.resultadoResta = num1 - num2;
            }
         }
    },
    data() {
        return {
            listaItems: [
                { id:1, nombre: 'Pepito', apellido: 'Perez'},
                { id:2, nombre: 'Mara', apellido: 'Fernandez'},
                { id:3, nombre: 'Lía', apellido: 'Rodriguez'},
                { id:4, nombre: 'Marcos', apellido: 'Castro'},
                { id:5, nombre: 'Xiana', apellido: 'Álvarez'}
            ],
            contador: 0,
            numero1: 0,
            numero2: 0,
            resultadoResta: 0,
            resultadoSuma: 0,
            msg: 'Mn'
        };
    }
}
</script>

<style>
button {
    background-color: darkblue;
    color: white;
}
</style>