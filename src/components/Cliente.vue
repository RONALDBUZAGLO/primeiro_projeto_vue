<template>
    <div id="cliente">
       <h4>Nome: {{nome}}</h4>
       <hr>
       <p> {{descricao}} </p>
       <hr>
       <p>Número: {{numero}} </p>
       <p>E-mail: {{email}} </p>
       <p>Idade: {{idade}} </p>
    </div>
</template>

<script>
export default {
    data(){
        return {
            
            descricao:"Lorem ipsumasdljkasldkjasldkj",
            numero: "asdasdasd",
            email: "asdlkajsdlkj@lkjsdlajk",
            idade: 30,
        }
    },
    props:{
        nome: String,
    }
}
</script>

<style scoped>
#cliente{
    background: #B8E9FF;
    margin: 1% auto;
    width: fit-content;
    padding: 1% 10%;
}

</style>

