<template>
    <div class="teclado">
        <button 
        class="teclado-botao" v-for="(letra, key) in 'abcdefghijklmnopqrstuvwxyz'" 
        :key="key"
        :disabled="verificarLetra(letra)"
        v-on:click="jogar(letra)"
        >
        {{letra}}
        </button>
 
    </div>
</template>

<script>
export default {
    name:'Teclado',
    props:{
        letras: Array,
        verificarLetra: Function,
        jogar: Function
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
    .teclado{
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        width: 80%;
        margin-top: 20px;
    }
    .teclado-botao{
        text-transform: uppercase;
        margin: 5px;
    }

</style>