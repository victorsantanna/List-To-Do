<template>
    <button class="clear" @click="clearTodos" >Limpar tudo </button>
</template>

<script>
export default {
    props:{
        todos: Array,
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
    background-color: #35d1dc;
    border: 1px solid #35d1dc;
    display: block;
    margin: auto;
    margin-top: 20px;
    width: 20%;
    font-size: 19px;
}

</style>