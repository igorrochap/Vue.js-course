<template>
  <div id="app">

    <h3>Cadastro: </h3>
    <small id="erro_nome" v-show="nameError">Campo vazio, por favor preencha</small><br>
    <input type="text" placeholder="Nome" v-model="nameField"><br>
    <input type="email" placeholder="Email" v-model="emailField"><br>
    <input type="number" placeholder="Idade" v-model="ageField"><br>
    <button @click="cadastrarCliente">Cadastrar</button>

    <hr>
    <div v-for="(cliente, index) in sortClientes" :key="cliente.id">
      <h4>{{ index }}</h4>
      <hr>
      <Cliente 
        :cliente="cliente"
        :showAge="true"
        @delete="deletarCliente($event)"
      />
    </div>
  </div>
</template>

<script>
import _ from 'lodash';
import Cliente from './components/Cliente';
//import Produto from './components/Produto';

export default {
  name: 'App',
  data(){
    return{
      nameError: false,
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
      if(this.nameField == "" || this.nameField == " " || this.nameField.length < 2){
        this.nameError = true;
      }
      else{
        this.clientes.push({
          id: Date.now(),
          nome: this.nameField,
          email: this.emailField,
          idade: this.ageField
        });

        this.nameError = false;
        this.nameField = "";
        this.emailField = "";
        this.ageField = 0;
      }
    },
    deletarCliente: function($event){
      //console.log($event);
      console.log('recebendo evento');
      let id = $event.cli_id;
      let newArray = this.clientes.filter(cliente => cliente.id != id);
      this.clientes = newArray;
    }
  },
  computed: {
    sortClientes: function(){
      return _.orderBy(this.clientes, ['nome'], ['asc']);
    }
  }
}
</script>

<style>
  #erro_nome{
    color: red;
  }
</style>
