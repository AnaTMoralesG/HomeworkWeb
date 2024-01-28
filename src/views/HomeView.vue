<!-- setup identificador del composition api -->
<script setup lang="ts">
import { ref } from 'vue';


const name = ref('');
const lastname = ref('');
const age=ref();
const gender=ref();
const genderInput=ref();

const nameError= ref(false)
const errorLastname=ref(false)
const ageError= ref(false)

const NameValidation = () => {
  if(name.value.trim().length >= 5 && name.value.trim().length <= 18){
    nameError.value = false;
    
  } else{
    nameError.value = true;
  }
}

const LastnameValidation= () => {
  if(lastname.value.trim() !== name.value.trim()){
    errorLastname.value = false;
  } else{
    errorLastname.value = true;
  }
}

const AgeValidation = () => {
  if(age.value > 0 && age.value <= 60){
    ageError.value = false;
    
  } else{
    ageError.value = true;
  }
}

const confirm = () => {
  alert('Datos Guardados (mentira) ( •̀ ω •́ )✧')
}


</script>

<template>
  <main>
    <h1>Hello（＾∀＾●）ﾉｼ</h1>
    <h2>Nombre:</h2>
    <input class="input" @input="NameValidation()" type="text" v-model="name" placeholder="Ana Teresa" >
    <h3 class="error" v-if="nameError">El nombre debe tener entre 5 a 18 caracteres ＼(ﾟｰﾟ＼)</h3>

    <h2>Apellido:</h2>
    <input class="input" @input="LastnameValidation()" type="text" v-model="lastname" placeholder="Morales García">
    <h3 class="error" v-if="errorLastname">El apellido no debe ser igual al nombre (。_。)</h3>

    <h2>Edad:</h2>
    <input class="input" @input="AgeValidation()" type="number" v-model="age" placeholder=18>
    <h3 class="error" v-if="ageError">La edad debe ser mayor a 0 y menor a 60 (っ °Д °;)っ</h3>


    <h2>Género:</h2>
    <select class="input" v-model="gender">
      <option value="male">Masculino</option>
      <option value="female">Femenino</option>
      <option value="other">Otro</option>
    </select>
    <input  class="input-other" type="text" v-if="gender === 'other'" v-model="genderInput">

    <div class="button-class" @click='confirm'>
      <button>Confirmar</button>
    </div>
  </main>
</template>

<style>

main{
  margin-top: 10px;
  border-width: 10px;
  border-radius: 10px;
  background-color: #ffffff20;
  padding: 40px;
}

h2{
  margin-top: 10px;
  margin-bottom: 6px;
  font-size: 18px;
}

.error{
  color: red;
  font-size: 14px;
  margin-top: 3px;
}

.input{
  background-color: #ffffff;
  border: none;
  border-radius: 5px;
  padding: 9px;
  width: 100%;
  margin-bottom: 6px;
}

.input-other{
  background-color: #ffffff;
  border: none;
  border-radius: 5px;
  padding: 9px;
  width: 100%;
  margin-top: 6px;
}

button{
  background-color: #009c5b;
  display: flex;
  justify-content: center;
  border: 2px #009c5b00 solid;
  border-radius: 5px;
  width: 100%;
  padding: 10px;
  margin-top: 30px;
  font-weight: 600;
}

button:hover{
  cursor: pointer;
  background-color: #009c5b00;
  border: 2px #009c5b solid;
  color: #ffffff;
}

.button-class{
  display: flex;
  justify-content: center;
}

</style>


<!-- Actividad: Realizar un formulario 
  donde se validen los siguientes datos
dependiendo de las entradas de datos:
Nombre -> validar mínimo 5 caracteres máximo 18
Apellido -> Validr que no sea igual al Nombre
Edad -> Validr que sea mayor a 0 y menor a 60
Genero -> 3 -> Masculino, femenino, otro. ->al seleccionar otro, puedas agregar el genero -->