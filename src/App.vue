<template>
  <div id="app">
    <h1>jogo da forca WDEV</h1>
    <section class="inicio" v-if="tela === 'inicio'">
      <formulario v-if="etapa === 'palavra'" formularioTitulo="defina a palavra" formularioBotao="próximo" :action="setPalavra"/>
      <formulario v-if="etapa === 'dica'" formularioTitulo="defina a dica" formularioBotao="iniciar o jogo" :action="setDica"/>
    </section>

    <section class="jogo" v-if="tela === 'jogo'">
      <jogo :erros="erros" :palavra="palavra" :dica="dica" :verificarLetra="verificarLetra" :etapa="etapa" :letras="letras" :jogar="jogar" :jogarNovamente="jogarNovamente"/>
    </section>
  </div>
</template>

<script>

import './css/global.css';
import formulario from './components/formulario.vue'
import jogo from './components/jogo.vue'

export default {
  name: 'App',
  components: {
    formulario,
    jogo
  },
  data(){
    return{
      tela: 'inicio',
      etapa: 'palavra',
      palavra: '',
      dica: '',
      letras: [''],
      erros: 0
    }
  },
   methods: {
    setPalavra: function(palavra){
      this.palavra = palavra;
      this.etapa = 'dica'
    },
    setDica: function(dica){
      this.dica = dica;
      this.tela = 'jogo';
      this.etapa = 'jogo';
    },
    verificarLetra: function(letra){
      return this.letras.find(item => item.toLowerCase() === letra.toLowerCase());
    },
    jogar: function(letra){
      //adiciona letra jogada
      this.letras.push(letra);

      //verificar erro
      this.verificarErros(letra);
    },
    verificarErros: function(letra){
      //acertos
      if(this.palavra.toLowerCase().indexOf(letra.toLowerCase()) >= 0)
      {
        return this.verificaAcertos;
      }

      //erros
      this.erros++;

      //enforcado
      if(this.erros===6)
      {
        this.etapa = 'enforcado';
      }
    },
    verificaAcertos: function(){
      let letrasUnicas = [...new Set(this.palavra.split(''))];
      if(letrasUnicas.length === (this.letras.length - this.erros)){
        this.etapa = 'ganhador';
      }
    },
    jogarNovamente: function(){
      this.palavra = '';
      this.dica = '';
      this.erros = 0;
      this.letras = [];
      this.tela = 'inicio';
      this.etapa = 'palavra';
    }
  }
}
</script>

<style>
#app {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
