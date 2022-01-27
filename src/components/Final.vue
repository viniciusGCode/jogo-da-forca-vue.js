<template>
    <div class="final">
        <div 
        :class="`final-texto ${etapa}`"
        > 
            {{texto}}
        </div>
        <button 
        class="final-botao"
        v-on:click="jogarNovamente"
        >Jogar de novo</button>
    </div>
</template>

<script>
export default {
    name:'Final',
    props:{
        etapa: String,
        texto: String,
        jogarNovamente: Function
    },
    data(){
        return{
        }
    },
    methods:{
        
    }
}
</script>

<style>
    .final-texto{
        margin: 20px 0px;
        font-size: 25px;
        font-weight: bold;
    }

    .final-texto.ganhador{
        color: var(--color-text-success);
    }

    .final-texto.enforcado{
        color: var(--color-text-error);
    }

</style>