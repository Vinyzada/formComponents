<script setup>

</script>

<template>
    <div class="w-screen h-screen flex justify-center px-10">
        <form action="" class="flex flex-col bg-white w-4/5 items-center">
            <div class="textChroma mb-14">Cadastro</div>
            <div class="flex gap-1 w-full">
                <div class="flex flex-col input w-full">
                    <input type="text" id="userName" required>
                    <span>Nome</span>
                </div>
                <div class="flex flex-col input w-1/3">
                    <input type="date" id="userDataNasc" required>
                    <span>Nascimento</span>
                </div>
                <div class="flex items-start 1/6 justify-center pt-2">
                    <div class="flex gap-2">
                        <input type="radio" id="sexMasc" name="sexMasc"><label for="sexMasc" class="mr-5">Masculino</label>
                    </div>
                    <div class="flex gap-2">
                        <input type="radio" id="sexFem" name="sexFem"><label for="sexFem">Feminino</label>
                    </div>
                </div>
            </div>
            <div class="flex w-full gap-4">
                <div class="flex flex-col input w-auto">
                    <input type="number" id="userTell" required>
                    <span>Telefone</span>
                </div>
                <div class="flex flex-col input w-4/5">
                    <input type="email" id="userEmail" required>
                    <span>Email</span>
                </div>
            </div>
            <div class="flex w-full gap-4">
                <div class="flex flex-col input w-full">
                    <input type="number" id="userCEP" required>
                    <span>CEP</span>
                </div>
                <div class="flex flex-col input w-full">
                    <input type="text" id="userCity" required>
                    <span>Cidade</span>
                </div>
            </div>
            <div class="flex w-full gap-4">
                <select name="estado" id="estado" class="w-1/6">
                    <option value="teste">estado</option>
                </select>
                <div class="flex flex-col input w-full">
                    <input type="text" id="userAdress" required>
                    <span>endereco</span>
                </div>
            </div>
            <div class="flex w-full gap-4">
                <div class="flex flex-col input w-1/2">
                    <input type="password" id="userPassword" required>
                    <span>senha</span>
                </div>
                <div class="flex flex-col input w-1/2">
                    <input type="password" id="userConfirmPassword" required>
                    <span>confirme sua senha</span>
                </div>
            </div>
            <div class="flex justify-between w-full px-4">
                <div class="hobbies">
                    <h3>hobbies</h3>
                    <div><input type="checkbox" id="hobbieMusic"><label for="hobbieMusic">Musica</label></div>
                    <div><input type="checkbox" id="hobbieWorkout"><label for="hobbieWorkout">Exercitar-se</label></div>
                    <div><input type="checkbox" id="hobbieSwim"><label for="hobbieSwim">Nadar</label></div>
                    <div><input type="checkbox" id="hobbieTravel"><label for="hobbieTravel">Viajar</label></div>
                    <div><input type="checkbox" id="hobbieSport"><label for="hobbieSport">Esporte</label></div>
                </div>
                <div class="lingprog">
                    <h3>linguagem de programacao</h3>
                    <div><label for="lingJs">JavaScript</label><input type="radio" id="lingJs"></div>
                    <div><label for="lingPHP">PHP</label><input type="radio" id="lingPHP"></div>
                    <div><label for="lingJava">Java</label><input type="radio" id="lingJava"></div>
                    <div><label for="lingPy">Python</label><input type="radio" id="lingPy"></div>
                    <div><label for="lingHTML">HTML</label><input type="radio" id="lingHTML"></div>
                </div>
            </div>
            <div class="flex w-full mt-10">
                <div class="flex flex-col input w-full">
                    <input type="text" id="userBio" required>
                    <span>bio</span>
                </div>
            </div>
            <input type="submit" value="Enviar" class="self-start bg-pink text-white font-semibold p-1 w-64 rounded-full my-10">
        </form>
    </div>
</template>

<style scoped>
.textChroma{
    font-size: 64px;
    font-weight: bold;
    background-clip: text;
    background-image: linear-gradient(90deg, #a0a0a0 46%, #ff84f3 100%);
    color: transparent;
    text-align: center;
    width: 300px;
}
.input{
    margin: 10px;
}
.input input{
    background: transparent;
    z-index: 2;
    border-bottom: 1px solid #ff84f3;
    padding: 0px 10px;
}
.input input:focus-visible{
    outline: 1px solid transparent;
}
.input input:focus + span,
.input input:valid + span{
    transform: translate(10px,-40px);
    color: #ff84f369;
    font-size: 12px;
}
.input span{
    z-index: 1;
    transform: translate(10px,-30px);
    transition: .1s linear;
}
select{
    margin-left: 7px;
    height: 35px;
    border: 1px solid white;
    border-bottom: 1px solid #ff84f3;
}
.hobbies div{
    display: flex;
    gap: 10px;
}
.lingprog div{
    display: flex;
    justify-content: end;
    gap: 10px;
}
input[type="date"]{
    appearance: none;
}
</style>