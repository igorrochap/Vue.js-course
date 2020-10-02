<template>
    <div :class="{'cliente' : !isPremium, 'cliente-premium' : isPremium}">
        <h4>Nome: {{ cliente.nome | nameProcessor}}</h4>
        <hr>
        <p>Email: {{ cliente.email }}</p>
        <!--<p v-show="showAge === true">Idade: {{ cliente.idade }}</p>-->
        <p v-if="showAge === true">Idade: {{ cliente.idade }}</p>
        <p v-else>A idade do usuário é privada</p>

        <button @click="colorChange($event)">Mudar status</button>
        <button @click="deleteEmission">Delete</button>
    </div>
</template>

<script>
    export default {
        data(){
            return{
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
        },
        methods: {
            colorChange: function(event){
                console.log(event);
                this.isPremium = !this.isPremium;
            },
            deleteEmission: function(){
                this.$emit('delete', {
                    cli_id: this.cliente.id,
                    component: this
                });
            },
            teste: function(){
                console.log('Teste no dale');
            }
        },
        filters: {
            nameProcessor: function(value){
                return value.toUpperCase();
            }
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
        background-color: black;
        color: rgb(255, 166, 0);    
        max-width: 600px;
        height: 180px;
        padding: 2%;
        margin-top: 2%;
    }
</style>