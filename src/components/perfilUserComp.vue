<script setup>
defineProps(['user'])
</script>
<template>
    <div class="w-screen h-screen flex justify-center px-10 flex-col items-center">
        <div class="textChroma flex mb-14">Perfil</div>
        <div class="flex gap-1 w-full">
            <div class="flex flex-col input w-full">
                <input type="text" id="userName" disabled :value="user.nome" />
                <span>Nome</span>
            </div>
            <div class="flex flex-col input w-1/3">
                <input type="text" id="userDataNasc" onfocus="(this.type='date')" onblur="(this.type='text')"
                    :value="user.datanasc" disabled />
                <span>Nascimento</span>
            </div>
            <div class="flex flex-col input w-1/3">
                <input type="text" id="userDataNasc" :value="user.sexo" disabled />
                <span>Sexo</span>
            </div>
        </div>
        <div class="flex w-full gap-4">
            <div class="flex flex-col input w-auto">
                <input type="tel" id="userTell" maxlength="9" minlength="9" :value="user.number"
                    oninput="this.value = this.value.replace(/[^0-9.]/g, '').replace(/(\..?)\../g, '$1');" disabled />
                <span>Telefone</span>
            </div>
            <div class="flex flex-col input w-4/5">
                <input type="text" id="userEmail" :value="user.email" disabled />
                <span>Email</span>
            </div>
        </div>
        <div class="flex w-full gap-4">
            <div class="flex flex-col input w-full">
                <input type="text" disabled :value="user.cep" />
                <span>CEP</span>
            </div>
            <div class="flex flex-col input w-full">
                <input type="text" id="userCity" :value="user.cidade" disabled />
                <span>Cidade</span>
            </div>
        </div>
        <div class="flex w-full gap-4">
            <div class="flex flex-col input w-full">
                <input type="text" name="" id="" :value="user.estado" disabled />
                <span>estado</span>
            </div>
            <div class="flex flex-col input w-full">
                <input type="text" id="userAdress" :value="user.endereco" disabled />
                <span>endereco</span>
            </div>
        </div>
        <div class="flex w-full gap-4">
            <div class="flex flex-col input w-1/2">
                <input type="password" id="userPassword" :value="user.senha" disabled />
                <span>senha</span>
            </div>
            <div class="flex flex-col input w-1/2">
                <input type="text" id="userLinguage" :value="user.linguage" disabled />
                <span>linguagem favorita</span>
            </div>
            <div class="flex flex-col input w-1/2">
                <input type="text" id="userLinguage" :value="user.hobbies" disabled />
                <span>hobbies</span>
            </div>
        </div>
        <input
        type="submit"
        value="Editar"
        @click="$emit('voltar')"
        class="self-start bg-pink text-white font-semibold p-1 w-64 rounded-full my-10"
        />
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

.input input+span {
    transform: translate(10px, -40px);
    color: #ff84f369;
    font-size: 12px;
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

select:invalid {
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