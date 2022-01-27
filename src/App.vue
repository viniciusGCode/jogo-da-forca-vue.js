<template>
  <div id="app">
    <h1>Jogo da forca</h1>

    <section v-if="tela === 'inicio'" id="inicio">
      <Formulario
      v-if="etapa == 'palavra'"
      title='Digite a Palavra'
      button='Próximo'
      :action="setPalavra"/>

      <Formulario 
      v-if="etapa == 'dica'"
      title='Digite a dica'
      button='Iniciar'
      :action="setDica"/>
    </section>

    <section v-if="tela === 'jogo'" id="jogo">
      <Jogo
      :erros="erros"
      :palavra="palavra"
      :dica="dica"
      :verificarLetra="verificarLetra"
      :letras="letras"
      :etapa="etapa"
      :jogar="jogar"
      :jogarNovamente="jogarNovamente"
      />
    </section>

  </div>
</template>

<script>

import './css/global.css';
import Formulario from './components/Formulario.vue';
import Jogo from './components/Jogo.vue';

export default {
  name: 'App',
  data(){
    return{
      tela: "inicio",
      etapa: "palavra",
      palavra: '',
      dica: '',
      erros: 0,
      letras: []
    }
  },
  components: {
    Formulario,
    Jogo
  },
  methods:{

    setPalavra: function(palavra){
      this.palavra = palavra;
      this.etapa = 'dica';
    },

    setDica: function(dica){
      this.dica = dica;
      this.etapa = 'jogo';
      this.tela = 'jogo';
    },

    verificarLetra: function(letra){
      return this.letras.find(item => item.toLowerCase() === letra.toLowerCase());
    },
    jogar: function(letra){
      //adiciona letra
      this.letras.push(letra);
      //valida o erro
      this.verificarErros(letra);

    },
    verificarErros: function(letra){
      //acerto
      if(this.palavra.toLowerCase().indexOf(letra.toLowerCase()) >= 0){
        return this.verificarAcertos();
      }
      //erros
      this.erros++;

      //enforcado

      if(this.erros === 6){
        this.etapa = 'enforcado';
      }

    },
    verificarAcertos: function(){
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
#app{
  display: flex;
  width: 100%;
  height: 100%;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

</style>
