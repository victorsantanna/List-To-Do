<template>

<section class="todo-list">

  <h3>Lista de Tarefas</h3>
    
  <div class="input-todo">
    <input type="text" placeholder="Digite sua tarefa" v-model="newTodo.text" @keyup.enter="addTodo"> 
    <button class="add" @click="addTodo()"> Adicionar </button>
  </div>
      
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

        
    </div>
  
      <limparTudo  @clear="clearAllTodos" v-if="todos.length" />

    
    
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

section{
    font-family: Tahoma, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin-top: 60px;
    display: flex;
    flex-direction: column;
    align-items: center;
  
}

 h3{
   font-size: 30px;
}

.all-todo .single-todo p{
    font-size: 19px;
    font-weight:500;
    color: #2c3e50;
}

.all-todo .single-todo.done p {
    text-decoration: line-through;
    text-decoration-thickness: 2px; 

}

input {
    font-family: Verdana, sans-serif;
    font-size: 16px;
    box-sizing: border-box;
    height: 40px;
    border-radius: 10px;
    width: 300px;
    border: 1px solid lightgrey;
    margin-top: 12px;
}

button {
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    font-size: 15px;
    background-color: transparent;
    cursor: pointer;
    box-sizing: border-box;
    height: 37px;
    border-radius: 10px;
    color: #fff;
}

button.add {
    background-color: #007bff;
    border: 1px solid  #007bff;
    margin-left: 2px;
}
button.add:hover{
    background-color: rgb(54, 0, 248);
    border: 1px solid rgb(54, 0, 248);
}




@media  only screen and (max-width: 767px) {

  section, .input-todo{
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;

  }
    input {
      margin-bottom: 12px; 
      margin-top: 10px;
    }

    button.add {
      width: 300px;
      font-size: 17px;
    }

}



</style>
