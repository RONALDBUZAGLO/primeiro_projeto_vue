<template>
  <div id="app">
      <button class="button is-primary">Primary</button>

    <h1>Guia Clientes</h1>
    
    <!-- 
    <Cliente :cliente="clienteRonald" :showIdade="true"/>
    <Cliente :cliente="clienteRonald" :showIdade="false"/>
    <Cliente :cliente="clienteRonald" :showIdade="true"/> -->
    <!-- <Cliente nome="Buzaglo" email="buzaglo@ronald" idade="40" />
    <Cliente :nome="nomeDoRonald" email="ronald@ronald" idade="30" /> -->
    <h3>Cadastro</h3>
    <small id="nomeErro" v-show="deuErro">O nome é inválido, tente novamente</small><br>
    <input type="text" placeholder="nome" v-model="nomeField"> <br>
    <input type="email" placeholder="email" v-model="emailField"> <br>
    <input type="number" placeholder="idade" v-model="idadeField"> <br>
    <button @click="cadastrarUsuario()" > Cadastrar</button>
    <hr>


    <div v-for="(cliente,index) in clientes" :key="cliente.id">
      <h1>{{index+1}}</h1>
      <input type="text" v-model="cliente.nome" >
      <Cliente :cliente="cliente" @meDelete="deletarUsuario($event)" />
      <!-- <Cliente :cliente="cliente" :showIdade="true"/>   -->
    </div>
    
  </div>
  
  
</template>

<script>
// import _ from 'lodash';
import Cliente from './components/Cliente'

// import Produto from './components/Produto'
export default {
  name: 'App',
  data(){
    return{
      // nomeDoRonald:"Ronald Buzaglo",
      // clienteRonald:{
      //   nome:"Victor Lima",
      //   email:"Vitor@victor",
      //   idade:99
      // }
      deuErro:false,
      nomeField:"",
      emailField:"",
      idadeField:0,
      clientes:[
        {
          id:1,
          nome:"Ronald",
          email:"Ronald@Ronald",
          idade:20
        },
        {
          id:2,
          nome:"Buzaglo",
          email:"Buzaglo@Buzaglo",
          idade:30
        },
        {
          id:3,
          nome:"Pessoa",
          email:"Pessoa@Pessoa",
          idade:40
        },
      ]
    }
  },
  components:{
    Cliente
    // Produto,
  },
  methods:{
    cadastrarUsuario:function(){
      
      if(this.nomeField == ""){
        // console.log("erro de validação");
        this.deuErro = true;
      }else{
        this.deuErro = false;
        this.clientes.push({
          nome:this.nomeField,
          email:this.emailField,
          idade:this.idadeField,
          id:Date.now()
        })
      this.nomeField = ""
      this.emailField = ""
      this.idadeField = 0
      }
    },
    deletarUsuario: function($event){
      console.log("Recebendo evento");
      console.log($event);
      console.log(`
      ${$event.idDoCliente}
      `);
      // $event.componente.isPremium = true;
      // console.log($event.idDoCliente);
      // $event.componente.testar()
      var id = $event.idDoCliente;
      var novoArray = this.clientes.filter(cliente =>{
        return cliente.id != id;
      })
      this.clientes = novoArray;
    },
    // computed:{
    //   // orderClientes: function(){
    //   //   var a = _.orderBy(this.clientes,['id'],['desc']);
    //   //   return a;
    //   }
    // }
  }
}
</script>

<style>
#nomeErro{
  color:red;
}
</style>