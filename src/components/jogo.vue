<template>
    <div class="jogo">
        <forca :erros="erros"/>
        <palavra :palavra="palavra" :dica="dica" :verificarLetra="verificarLetra" :etapa="etapa"/>
        <teclado v-if="etapa === 'jogo'" :letras="letras" :verificarLetra="verificarLetra" :jogar="jogar"/>
        <final v-if="etapa != 'jogo'" :etapa="etapa" :texto="etapa=== 'ganhador' ? 'parabéns =)' : 'tadinho :('" :jogarNovamente="jogarNovamente"/>
    </div>
    
</template>

<script>

import forca from './forca.vue'
import palavra from './palavra.vue'
import teclado from './teclado.vue'
import final from './final.vue'

export default {
    name: 'jogo',
    components:{
        forca,
        palavra,
        teclado,
        final
     },
    props: {
        erros: Number,
        palavra: String,
        dica: String,
        verificarLetra: Function,
        etapa: String,
        letras: Array,
        jogar: Function,
        jogarNovamente: Function
    }
}
</script>

<style scoped>

.jogo{
    widows: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
}
</style>