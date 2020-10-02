<template>
  <div id="app">
    
    <div v-for="(cliente, index) in clientes" :key="cliente.id">
      <h4>{{ index }}</h4>
      <hr>
      <Cliente 
        :cliente="cliente"
        :showAge="true"
      />
      <hr>
      <input type="text" v-model="cliente.nome">
      <input type="text" v-model="cliente.email">
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
      clientes: [
        {
          id: 1,
          nome: 'Victor Lima',
          email: 'victor@lima.com',
          idade: 99
        },
        {
          id: 2,
          nome: 'Igor Rocha',
          email: 'igor@rocha.com',
          idade: 20
        },
        {
          id: 3,
          nome: 'João Jorge',
          email: 'joao@jorge.com',
          idade: 77
        },
        {
          id: 4,
          nome: 'Willian Butcher',
          email: 'billy@butcher.com',
          idade: 40
        },
        {
          id: 5,
          nome: 'Hughie Campbell',
          email: 'hughie@campbell.com',
          idade: 28
        }
      ]
    }
  },
  components: {
    Cliente,
    //Produto
  }
}
</script>

<style>

</style>
