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
        display: block;
        margin: auto;
        margin-top: 20px;
        width: 300px;
        font-size: 19px;
    }

    button.clear:hover{
        background-color: #f00018;
        border: 1px solid #f00018;
    }

@media (max-width: 661px){
    
    button.clear {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        margin-top: auto; 
        margin-bottom: auto; 
        width: 300px;
    }
}

</style>