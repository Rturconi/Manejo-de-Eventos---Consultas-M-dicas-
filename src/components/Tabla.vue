<script setup>

const props = defineProps({
    nombre: String,
    fecha: String,
    hora: String,
    gravedad: String,
    motivo: String,
})
</script>

<template>
    <div class="tableBox" :style="{backgroundColor: gravedad}">
        <table>
            <tr>
                <th>Paciente</th>
                <th>Fecha</th>
                <th>Hora</th>
                <th>motivo</th>
            </tr>
            <tr>
                <td>{{nombre}}</td>
                <td>{{fecha}}</td>
                <td>{{hora}}</td>
                <td>{{motivo}}</td>
            </tr>
        </table>
        <button @click="$emit('eliminarPaciente')">Eliminar</button>
    </div>

</template>

<style scoped>


.tableBox {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    border: 5px, solid, white;
    border-radius: 10px;
    box-shadow: 0px 4px 4px 2px rgba(0, 0, 0, 0.393);
}

table{
    width: 100%;
    text-align: center;
}
</style>
