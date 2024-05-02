<template>
<section class="todo-list">
    <h3>Lista de tarefas</h3>

    <input type="text" placeholder="Digite sua tarefa" v-model="newTodo.text" class="input-todo"> 
    <button class="add" @click="addTodo()">Adicionar</button>
      
    <div class="all-todo">
      <div 
      v-for="todo in todos" 
      :key="todo" 
      class="single-todo"
      :class="{done : todo.done}"
      >
        <p>{{ todo.text }}</p>
      </div>

    </div>

</section>


</template>

<script>
const todos = [
  {
    text: 'Aprender Html',
    done: false
  },
  {
    text: 'Aprender vuejs',
    done: false
  },
]


export default {
  name: 'App',
  data(){
    return{
      todos,
      newTodo:{
        done:false,
      }
    }
  },
  methods:{
    addTodo: function(){
      this.todos.push(this.newTodo);
      this.newTodo = {
        done: false
      };
    }
  }
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
  

}

input {
    box-sizing: border-box;
    height: 35px;
    border-radius: .40rem;
    width: 40%;
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
</style>
