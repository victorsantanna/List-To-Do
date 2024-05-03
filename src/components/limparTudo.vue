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
    width: 20%;
    font-size: 19px;
}

</style>