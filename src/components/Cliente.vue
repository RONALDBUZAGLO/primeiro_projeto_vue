<template>
    <div :class="{
        'cliente': !isPremium, 
        'cliente-premium': isPremium
        }">

       <h4>Nome: {{cliente.nome | processarEmail}}</h4>
       <p>E-mail: {{cliente.email}} </p>
       <p v-if="showIdade === true">Idade: {{cliente.idade}} </p>
       <p v-else >O usuário escondeu a idade</p>
       <button @click="mudarCor($event)" >Mudar cor</button>
       <button @click="emitirEventoDelete()" >Deletar</button>
       <h4>Id especial: {{idEspecial}}</h4>
    </div>
</template>

<script>
export default {
    data(){
        return {
            isPremium: false,
        }
    },
    props:{
        // nome: String,
        // email: String,
        // idade: Number,
        cliente: Object,
        showIdade:Boolean,

    },
    methods:{
        mudarCor: function($event){
            console.log($event);
            this.isPremium = !this.isPremium;
            // console.log(`
            // Chamando evento!
            // `);
        },
        emitirEventoDelete: function(){
            console.log("emitindo do filho");
            this.$emit("meDelete",{
                curso:"Formação Node.js",
                emPromocao:true,
                componente:this,
                idDoCliente:this.cliente.id,
            });
        },
        testar:function(){
            console.log("testando para valer");
            alert("Isso é um alert");
        }
    },
    filters:{
        processarEmail: function(value){
            return value.toUpperCase();
        }
    },
    computed:{
        idEspecial:function(){
            return (this.cliente.email + this.cliente.nome +this.cliente.id).toUpperCase();
        }
    }
}
</script>

<style scoped>
.cliente{
    background: #B8E9FF;
    margin: 1% auto;
    max-width: 400px;
    padding: 1% 10%;
    border-radius: 5%;
}
.cliente-premium{
    background: #58ff58;
    margin: 1% auto;
    max-width: 400px;
    padding: 1% 10%;
    border-radius: 5%;
}
</style>