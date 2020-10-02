<template>
    <div :class="{'cliente' : !isPremium, 'cliente-premium' : isPremium}">
        <h4>Nome: {{ cliente.nome }}</h4>
        <hr>
        <p>Email: {{ cliente.email }}</p>
        <!--<p v-show="showAge === true">Idade: {{ cliente.idade }}</p>-->
        <p v-if="showAge === true">Idade: {{ cliente.idade }}</p>
        <p v-else>A idade do usuário é privada</p>

        <button v-on:click="isPremium = true">Premium</button>
        <button v-on:click="isPremium = false">Normal</button>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                /*numero: "1234",
                email: "jorge1234@jorge.com",
                descricao: "Descrição",
                idade: 77*/
                isPremium: false,
            }
        },
        props: {
            //nome: String,
            //numero: String,
            //email: String,
            //descricao: String,
            //idade: Number,
            cliente: Object,
            showAge: Boolean
        }
    }
</script>

<style scoped>
    .cliente {
        background-color: rgb(177, 177, 177);    
        max-width: 600px;
        height: 180px;
        padding: 2%;
        margin-top: 2%;
    }

    .cliente-premium{
        background-color: rgb(255, 166, 0);    
        max-width: 600px;
        height: 180px;
        padding: 2%;
        margin-top: 2%;
    }
</style>