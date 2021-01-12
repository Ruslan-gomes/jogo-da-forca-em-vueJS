<template>
    <div class="teclado">
        <button class="teclado-button"
         v-for="(letra, key) in 'abcdefghijklmnopqrstuvwxyz'" :key="key"
          :disabled="verificarLetra(letra)" 
          @click="jogar(letra)">
            {{letra}}
        </button>
    </div>
</template>

<script>
export default {
    name: 'teclado',
    props: {
        letras: Array,
        verificarLetra: Function,
        jogar: Function
    }
}
</script>

<style scoped>

.teclado{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    max-width: 85%;
    margin-top: 20px;
}

.teclado-button{
    margin: 5px;
    text-transform: uppercase;
}
</style>