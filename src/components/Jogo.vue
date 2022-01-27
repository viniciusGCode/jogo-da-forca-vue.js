<template>
    
    <div class="jogo">
        
        <Forca
        :erros="erros"
        />

        <Palavra
        :palavra="palavra"
        :dica="dica"
        :verificarLetra="verificarLetra"
        :etapa="etapa"/>


        <Teclado
        v-if="etapa === 'jogo'"
        :letras="letras"
        :verificarLetra="verificarLetra"
        :jogar="jogar"
        />

        <Final
        v-if="etapa != 'jogo'"
        :etapa="etapa"
        :texto="etapa === 'ganhador' ? 'You win ;D' : 'You lose :C'"
        :jogarNovamente="jogarNovamente"
        />

        
    </div>

</template>

<script>
import Forca from './Forca';
import Palavra from './Palavra';
import Teclado from './Teclado';
import Final from './Final';



export default {
    name:'Jogo',
    props:{
        erros: Number,
        palavra: String,
        dica: String,
        verificarLetra: Function,
        etapa: String,
        letras: Array,
        jogar: Function,
        jogarNovamente: Function
    },
    data(){
        return{
        }
    },
    methods:{
        
    },
    components:{
        Forca,
        Palavra,
        Teclado,
        Final
    }
}
</script>

<style>

.jogo{
    display: flex;
    flex-direction: column;
    width: 100%;
    align-items: center;
    text-align: center;
}

</style>