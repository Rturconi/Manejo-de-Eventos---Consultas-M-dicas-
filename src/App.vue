<script setup>

import { ref } from 'vue'
import Tabla from './components/Tabla.vue';


const pacientes = ref([])

const paciente = ref({
  nombre: "",
  fecha: "",
  hora: "",
  gravedad: "",
  motivo: "",
})

const agregar = () => {
  pacientes.value.push({ ...paciente.value })
  console.log(pacientes.value);
  //resetea estado 
  paciente.value = {
    nombre: "",
    fecha: "",
    hora: "",
    gravedad: "",
    motivo: "",
  }

}

const quitarPaciente = (indice) => {
  pacientes.value.splice(indice, 1)
  console.log(pacientes.value);
}


// const btnDissable = () => {
//   if (paciente.nombre == ""
//     || paciente.fecha == ""
//     || paciente.hora == ""
//     || paciente.gravedad == ""
//     || paciente.motivo == "")
//     return true;
//   else return false
// }

</script>

<template>
  <h1 class="title">Ingreso de Consultas</h1>
  <div class="formBox">
    <form action="" @submit.prevent="default">
      <!-- PACIENTE -->
      <div class="formItem">
        <label for="" :class="{ 'redText': paciente.nombre == '' }">Paciente</label>
        <input type="text" v-model="paciente.nombre">
      </div>
      <!-- FECHA -->
      <div class="formItem">
        <label for="" :class="{ 'redText': paciente.fecha == '' }">Fecha</label>
        <input type="date" v-model="paciente.fecha">
      </div>
      <!-- HORA -->
      <div class="formItem">
        <label for="" :class="{ 'redText': paciente.hora == '' }">Hora</label>
        <input type="time" v-model="paciente.hora">
      </div>
      <!-- GRAVEDAD -->
      <div class="formItem">
        <label for="" :class="{ 'redText': paciente.gravedad == '' }">Gravedad</label>
        <select name="" id="" v-model="paciente.gravedad">
          <option value="palegreen">Baja</option>
          <option value="khaki">Media</option>
          <option value="indianred">Grave</option>
        </select>
      </div>
      <!-- MOTIVO -->
      <div class="formItem">
        <label for="" :class="{ 'redText': paciente.motivo == '' }">Motivo</label>
        <input type="text" v-model="paciente.motivo">
      </div>

    </form>
    <!-- BOTÓN -->
    <button @click="agregar" class="addBtn" 
    :disabled="(paciente.nombre == '')
      || (paciente.fecha == '')
      || (paciente.hora == '')
      || (paciente.gravedad == '')
      || (paciente.motivo == '')">Agregar
    </button>

  </div>

  <br>

  <div class="alert" v-show="pacientes.length == 0">
    <span class="redText">Aun no hay consultas registradas.</span>
  </div>
  

  <div v-for="(paciente, i) in pacientes">
    <Tabla :nombre="paciente.nombre" :fecha="paciente.fecha" :hora="paciente.hora" :gravedad="paciente.gravedad"
      :motivo="paciente.motivo" @eliminarPaciente="quitarPaciente(i)" />
    <br>
  </div>



</template>

<style>
* {
  font-family: Arial;
  font-size: 18px;
}

.title{
  text-align: center;
    color: #d7d7d7eb;
    font-size: 2rem;
    letter-spacing: 3px;
    font-weight: 800;
}

body {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 5% 10% 5% 10%;
  background-color: rgb(85, 141, 130);

}

.formBox {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
  border: 5px, solid, white;
  border-radius: 10px;
  background-color: rgb(124, 200, 185);
  box-shadow: 0px 4px 4px 2px rgba(0, 0, 0, 0.393);
}

form {
  display: flex;
  flex-direction: row;
  gap: 10px;
  margin-bottom: 30px;
}

.formItem {
  display: flex;
  flex-direction: column;
  text-align: center;

  input,
  select {
    padding-left: 2rem;
    padding-right: 2rem;
  }

  label {
    font-weight: bold;
  }
}

.addBtn {
  width: 200px;
  box-shadow: 0px 4px 4px 2px rgba(0, 0, 0, 0.393);
}

.alert{
  display: flex;
  justify-content: center;
}

.redText {
  color: crimson;
}

</style>
