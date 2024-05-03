<template>

<section class="todo-list">

  <h3>Lista de tarefas</h3>
    

    <input type="text" placeholder="Digite sua tarefa" v-model="newTodo.text" class="input-todo"  @keyup.enter="addTodo"> 
    <button class="add" @click="addTodo()"> Adicionar </button>
      
  <div class="all-todo">
      <div 
        v-for="todo in todos" 
        :key="todo" 
        class="single-todo"
        :class="{done : todo.done}"
        @click="todo.done = !todo.done"
      >
        <p>{{ todo.text }}</p>
      </div>

     <!--
       <button class="clear" @click="todos=[]" v-if="todos.length">Limpar Tudo</button>
     -->
     
        
      <limparTudo  @clear="clearAllTodos" v-if="todos.length" />
  </div>

</section>

</template>

<script>

import limparTudo from './components/limparTudo.vue'

const todos = []

export default {
  name: 'App',
  components:{
    limparTudo,
  },
  data(){
    return{
      todos,
      newTodo:{
        done:false,
      }
    }
  },
  methods:{
    clearAllTodos(){
      this.todos = [];
      localStorage.removeItem('todos');
    },
    addTodo(){
      if(this.newTodo.text){
        this.todos.push(this.newTodo);
        this.newTodo = {
          done: false
        };
       
      } else{
        alert('Por Gentileza Digite uma Tarefa!')
      }
    },
  },
  created(){
    this.todos = localStorage.getItem("todos") ? JSON.parse(localStorage.getItem("todos")) : this.todos;
  },
  updated(){
    localStorage.setItem("todos", JSON.stringify(this.todos))
  },
}

</script>

<style>
#app {
  
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.todo-list h3{
  font-size: 30px;
  font-family:Verdana, Geneva, Tahoma, sans-serif;
  margin-top: 30px;

}

.all-todo .single-todo p{
  font-size: 19px;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  color: #2c3e50;
}

.all-todo .single-todo.done p {
    text-decoration: line-through;
    text-decoration-thickness: 2px; 

}

input {
    box-sizing: border-box;
    height: 35px;
    border-radius: .40rem;
    width: 35%;
    border: 2px solid lightgrey;
    margin-top: 32px;
}

button {
    background-color: transparent;
    cursor: pointer;
    box-sizing: border-box;
    height: 34px;
    border-radius: .25rem;
    color: #fff;
}

button.add {
    background-color: #007bff;
    border: 1px solid  #007bff;
    margin-left: 2px;
}

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
