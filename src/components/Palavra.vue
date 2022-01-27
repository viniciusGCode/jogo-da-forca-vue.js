<template>

    <div class="palavra">
        
        <div class="palavra-letras">

            <div class="palavra-letra" v-for="(letra,key) in palavra" :key="key">
                {{ (verificarLetra(letra) || etapa === 'enforcado') ? letra : ''}}
            </div>

        </div>
    <div class="palavra-dica">
        {{dica}}

    </div>

    </div>

</template>

<script>

export default {
    name:'Palavra',
    props:{
        palavra: String,
        dica: String,
        verificarLetra: Function,
        etapa: String
    },
    data(){
        return{
        }
    },
    methods:{
    },
    components:{
    
    }
}
</script>

<style>

.palavra{
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    text-transform: uppercase;
}

.palavra-letras{
    display: flex;
    margin-bottom: 20px;
}

.palavra-letra{
    height: 30px;
    width: 30px;
    margin: 0px 5px;
    border-bottom: 1px solid var(--color-text-light);
    display: flex;
    justify-content: center;
    align-items: center;
}


</style>