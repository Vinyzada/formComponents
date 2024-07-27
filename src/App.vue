<script setup>
import { ref } from 'vue';
import authFormVue from './components/authForm.vue';
import perfilUser from './components/perfilUserComp.vue';

const viewPerfil = ref(false)
const user = ref({
    nome: '',
    email: '',
    sexo: '',
    senha: '',
    number: '',
    datanasc: '',
    endereco: '',
    cidade: '',
    estado: '',
    linguage: '',
    bio: [],
    cep: '',
})

function salvarInfo(info){
  user.value = info
  viewPerfil.value = !viewPerfil.value
}
function retornar(){
  viewPerfil.value = !viewPerfil.value
}

console.log(user.value.nome)
</script>

<template>
  <perfilUser :user="user" @voltar="retornar" v-if="viewPerfil"/>
  <authFormVue @salvar="salvarInfo" v-else/>
</template>

<style>
</style>