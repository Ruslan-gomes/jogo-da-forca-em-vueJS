<template>
    <div class="formulario">
        <div class="formulario-title">{{formularioTitulo}}</div>
        <input type="text" class="formulario-input" v-model="inputValue" @keyup.enter="onSubmit">
        <button class="formulario-button"
         :disabled="inputValue.length === 0"
         @click="onSubmit
         ">{{formularioBotao}}</button>
    </div>
</template>

<script>
export default {
    name: 'formulario',
    props: {
        formularioTitulo: String,
        formularioBotao: String,
        action: Function
    },
    data(){
        return{
            inputValue: ''
        }
    },
    methods: {
        onSubmit: function(){
            this.action(this.inputValue);
            this.inputValue = '';
        }
    }
}
</script>

<style scoped>

.formulario{
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    justify-content: center;
    margin-top: 20px;
}

.formulario-input{
    padding: 10px 5px;
    border: 0;
    border-radius: 5px;
    margin: 10px 0px;
    text-align: center;
    color: var(--color-text-dark);
    font-size: 15px;
}

</style>