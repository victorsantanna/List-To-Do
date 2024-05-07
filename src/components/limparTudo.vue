<template>
    <button class="clear" @click="clearTodos" >Limpar tudo </button>
</template>

<script>
export default {
    props:{
    
    },
    methods:{
        clearTodos(){
            this.$emit('clear');
        }
    }
    
};
</script>

<style scoped>
    button.clear {
        background-color: #dc3545;
        border: 1px solid #dc3545;      
        margin-top: 10px;
        width: 300px;
        font-size: 19px;
    }

    button.clear:hover{
        background-color: #f00018;
        border: 1px solid #f00018;
    }

@media only screen and (max-width: 767px){
    
    button.clear {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 300px;
    }
}

</style>