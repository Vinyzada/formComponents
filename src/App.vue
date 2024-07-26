<script setup>
import { ref } from 'vue';
import authFormVue from './components/authForm.vue';

const user = ref({
    nome: '',
    email: '',
    sexo: '',
    senha: '',
    datanasc: '',
    endereco: '',
    cidade: '',
    estado: '',
    bio: '',
    cep: '',
})

function salvarInfo(info){
  user.value = info
}
</script>

<template>
  <authFormVue :user="user" @salvar="salvarInfo"/>
</template>

<style>
</style>