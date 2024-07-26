<script setup>
import { ref } from 'vue';
const emit = defineEmits(['salvar'])

const estados = ([
  { 'name': 'Acre', 'sigla': 'AC' },
  { 'name': 'Alagoas', 'sigla': 'AL' },
  { 'name': 'Amapá', 'sigla': 'AP' },
  { 'name': 'Amazonas', 'sigla': 'AM' },
  { 'name': 'Bahia', 'sigla': 'BA' },
  { 'name': 'Ceará', 'sigla': 'CE' },
  { 'name': 'Distrito Federal', 'sigla': 'DF' },
  { 'name': 'Espírito Santo', 'sigla': 'ES' },
  { 'name': 'Goiás', 'sigla': 'GO' },
  { 'name': 'Maranhão', 'sigla': 'MA' },
  { 'name': 'Mato Grosso', 'sigla': 'MT' },
  { 'name': 'Mato Grosso do Sul', 'sigla': 'MS' },
  { 'name': 'Minas Gerais', 'sigla': 'MG' },
  { 'name': 'Pará', 'sigla': 'PA' },
  { 'name': 'Paraíba', 'sigla': 'PB' },
  { 'name': 'Paraná', 'sigla': 'PR' },
  { 'name': 'Pernambuco', 'sigla': 'PE' },
  { 'name': 'Piauí', 'sigla': 'PI' },
  { 'name': 'Rio de Janeiro', 'sigla': 'RJ' },
  { 'name': 'Rio Grande do Norte', 'sigla': 'RN' },
  { 'name': 'Rio Grande do Sul', 'sigla': 'RS' },
  { 'name': 'Rondônia', 'sigla': 'RO' },
  { 'name': 'Roraima', 'sigla': 'RR' },
  { 'name': 'Santa Catarina', 'sigla': 'SC' },
  { 'name': 'São Paulo', 'sigla': 'SP' },
  { 'name': 'Sergipe', 'sigla': 'SE' },
  { 'name': 'Tocantins', 'sigla': 'TO' },
  { 'name': 'Estrangeiro', 'sigla': 'EX' }
])

// GET CEP API **
const enderecoApi = ref('');
const cidade = ref('')
const estado = ref('');
const infoEndUser = ref('');
const cep = ref('')

const getAddress = async (cep) => {
  const apiUrl = `https://viacep.com.br/ws/${cep}/json/`
  const response = await fetch(apiUrl)
  cep = cep.value

  infoEndUser.value = await response.json()
  const bairro = ref(infoEndUser.value.bairro)
  const rua = ref(infoEndUser.value.logradouro)

  enderecoApi.value = `${rua.value} - ${bairro.value}`
  cidade.value = infoEndUser.value.localidade
  estado.value = infoEndUser.value.uf

  console.log(estado.value)
}
// **

const user = ref({
    nome: '',
    email: '',
    sexo: '',
    senha: '',
    number: '',
    datanasc: '',
    endereco: enderecoApi,
    cidade: cidade,
    estado: estado,
    linguage: '',
    bio: '',
    cep: cep,
})
const viewPerfil = ref(0)
function salvar(){
    emit('salvar', { ...user.value });
    viewPerfil.value++
  }
</script>

<template>
  <div class="w-screen h-screen flex justify-center px-10">
    <form @submit.prevent="salvar" class="flex flex-col bg-white w-3/4 items-center">
      <div class="textChroma mb-14" v-if="viewPerfil==0">Cadastro</div>
      <div class="textChroma mb-14" v-else>Editando Perfil</div>
      <div class="flex gap-1 w-full">
        <div class="flex flex-col input w-full">
          <input type="text" id="userName" required v-model="user.nome" />
          <span>Nome</span>
        </div>
        <div class="flex flex-col input w-1/3">
          <input
            type="text" id="userDataNasc" onfocus="(this.type='date')" onblur="(this.type='text')" v-model="user.datanasc" required/>
          <span>Nascimento</span>
        </div>
        <div class="flex items-start 1/6 justify-center pt-2">
          <div class="flex gap-2">
            <input type="radio" id="sexMasc" name="sex" value="masculino" v-model="user.sexo" required /><label for="sexMasc" class="mr-5">Masculino</label>
          </div>
          <div class="flex gap-2">
            <input type="radio" id="sexFem" name="sex" value="feminino" v-model="user.sexo" /><label for="sexFem">Feminino</label>
          </div>
        </div>
      </div>
      <div class="flex w-full gap-4">
        <div class="flex flex-col input w-auto">
          <input type="tel" id="userTell" maxlength=9 minlength=9 v-model="user.number" oninput="this.value = this.value.replace(/[^0-9.]/g, '').replace(/(\..*?)\..*/g, '$1');" required  />
          <span>Telefone</span>
        </div>
        <div class="flex flex-col input w-4/5">
          <input type="text" id="userEmail" v-model="user.email" required />
          <span>Email</span>
        </div>
      </div>
      <div class="flex w-full gap-4">
        <div class="flex flex-col input w-full">
          <input type="text" id="userCEP" minlength="8" maxlength="8" v-model="cep" @focusout="getAddress(cep)" oninput="this.value = this.value.replace(/[^0-9.]/g, '').replace(/(\..*?)\..*/g, '$1');" required />
          <span>CEP</span>
        </div>
        <div class="flex flex-col input w-full">
          <input type="text" id="userCity" v-model="user.cidade" required />
          <span>Cidade</span>
        </div>
      </div>
      <div class="flex w-full gap-4">
        <select name="estado" v-model="user.estado" required>
            <option value="" disabled>estado</option>
            <option v-for="(estado, index) in estados" :key="index" :value="estado.sigla">
                {{ estado.name }} - {{ estado.sigla }}
            </option>
        </select>
        <div class="flex flex-col input w-full">
          <input type="text" id="userAdress" v-model="user.endereco" required />
          <span>endereco</span>
        </div>
      </div>
      <div class="flex w-full gap-4">
        <div class="flex flex-col input w-1/2">
          <input type="password" id="userPassword" v-model="user.senha" required />
          <span>senha</span>
        </div>
        <div class="flex flex-col input w-1/2">
          <input type="password" id="userConfirmPassword" required />
          <span>confirme sua senha</span>
        </div>
      </div>
      <div class="flex justify-between w-full px-4">
        <div class="hobbies">
          <h3 class="font-semibold py-2">hobbies</h3>
          <div>
            <input type="checkbox" id="hobbieMusic" /><label for="hobbieMusic">Musica</label>
          </div>
          <div>
            <input type="checkbox" id="hobbieWorkout" /><label for="hobbieWorkout">Exercitar-se</label>
          </div>
          <div><input type="checkbox" id="hobbieSwim" /><label for="hobbieSwim">Nadar</label></div>
          <div>
            <input type="checkbox" id="hobbieTravel" /><label for="hobbieTravel">Viajar</label>
          </div>
          <div>
            <input type="checkbox" id="hobbieSport" /><label for="hobbieSport">Esporte</label>
          </div>
        </div>
        <div class="lingprog">
          <h3 class="font-semibold py-2">linguagem de programacao</h3>
          <div><label for="lingJs">JavaScript</label><input type="radio" id="lingJs" name="lingprog" value="JavaScript" v-model="user.linguage" required/></div>
          <div><label for="lingPHP">PHP</label><input type="radio" id="lingPHP" name="lingprog" value="PHP" v-model="user.linguage" required/></div>
          <div><label for="lingJava">Java</label><input type="radio" id="lingJava" name="lingprog" value="Java" v-model="user.linguage" required/></div>
          <div><label for="lingHTML">HTML</label><input type="radio" id="lingHTML" name="lingprog" value="HTML" v-model="user.linguage" required/></div>
          <div><label for="lingPy">Python</label><input type="radio" id="lingPy" name="lingprog" value="Python" v-model="user.linguage" required/></div>
        </div>
      </div>
      <div class="flex w-full mt-10">
        <div class="flex flex-col input w-full">
          <input type="text" id="userBio" v-model="user.bio" />
          <span>bio</span>
        </div>
      </div>
      <input
        type="submit"
        value="Enviar"
        class="self-start bg-pink text-white font-semibold p-1 w-64 rounded-full my-10"
      />
    </form>
  </div>
</template>

<style scoped>
.textChroma {
  font-size: 64px;
  font-weight: bold;
  background-clip: text;
  background-image: linear-gradient(90deg, #a0a0a0 46%, #ff84f3 100%);
  color: transparent;
  text-align: center;
  width: 300px;
}
.input {
  margin: 10px;
}
.input input {
  background: transparent;
  z-index: 2;
  border-bottom: 1px solid #ff84f3;
  padding: 0px 10px;
}
.input input:focus-visible {
  outline: 1px solid transparent;
}
.input input:focus + span,
.input input:valid + span {
  transform: translate(10px, -40px);
  color: #ff84f369;
  font-size: 12px;
}
.input input:invalid{
    color: red;
    font-weight: semibold;
    border-bottom: 1px solid #ff0000;
}
.input input:invalid + span{
    font-weight: semibold;
}
.input span {
  z-index: 1;
  transform: translate(10px, -30px);
  transition: 0.1s linear;
}
select {
  margin-left: 7px;
  height: 35px;
  border: 1px solid white;
  border-bottom: 1px solid #ff84f3;
}
select:invalid{
    border-bottom: 1px solid #ff0000;
}
.hobbies div {
  display: flex;
  gap: 10px;
}
.lingprog div {
  display: flex;
  justify-content: end;
  gap: 10px;
}
input[type='date'] {
  appearance: none;
}
</style>
