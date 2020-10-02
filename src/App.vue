<template>
  <div id="app">

    <h3>Cadastro: </h3>
    <input type="text" placeholder="Nome" v-model="nameField"><br>
    <input type="email" placeholder="Email" v-model="emailField"><br>
    <input type="number" placeholder="Idade" v-model="ageField"><br>
    <button @click="cadastrarCliente">Cadastrar</button>

    <hr>
    <div v-for="(cliente, index) in clientes" :key="cliente.id">
      <h4>{{ index }}</h4>
      <hr>
      <Cliente 
        :cliente="cliente"
        :showAge="true"
      />
    </div>
  </div>
</template>

<script>
import Cliente from './components/Cliente';
//import Produto from './components/Produto';

export default {
  name: 'App',
  data(){
    return{
      nameField: "",
      emailField: "",
      ageField: 0,
      clientes: [
        {
          id: 1,
          nome: 'Igor Rocha',
          email: 'igor@rocha.com',
          idade: 20
        },
      ]
    }
  },
  components: {
    Cliente,
    //Produto
  },
  methods: {
    cadastrarCliente: function(){
      this.clientes.push({
        id: Date.now(),
        nome: this.nameField,
        email: this.emailField,
        idade: this.ageField
      });

      this.nameField = "";
      this.emailField = "";
      this.ageField = 0;
    }
  }
}
</script>

<style>

</style>
