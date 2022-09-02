<template>
  <div>
  <div id="header">
    <Search v-on:query-change="querySearch"/>
  </div>

    <div id="main-container">
      <h2> Lista de Pendientes </h2>
      <TodoAdd v-on:add-todo="addTodo" />
      <Todos v-bind:todoslist="copyTodos" v-on:delete-todo="deleteTodo" />
    </div>
  </div>
</template>

<script id="script">
//import HelloWorld from './components/HelloWorld.vue'
import Search from './components/Search'
import Todos from './components/Todos'
import TodoAdd from './components/TodoAdd';

export default {
  name: 'App',
  components: {
    Search,
    Todos,
    TodoAdd,
},
  methods:{
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id != id);
      this.copyTodos = [... this.todos];
    },
    addTodo(todo){
            this.todos.push(todo);
            this.copyTodos = [... this.todos];
        },
        querySearch(query){
          if(query.trim() === ''){
            this.copyTodos = [... this.todos];
          } else{
            const temp = this.todos.filter(todo =>{
              return todo.title.includes(query)
            });
            this.copyTodos = [... temp];
          }
        }
  },
  data() {
    return {
      todos: [
        {
          id: 0,
          title: 'comprar la cena',
          completed: false,
        },
        {
          id: 1,
          title: 'Sacar a pasear el perro',
          completed: false,
        },
        {
          id: 2,
          title: 'Jugar Xbox',
          completed: false,
        },
        {
          id: 3,
          title: 'Limpiar casa',
          completed: false,
        }
      ],
      copyTodos: []
    }
  },
  created() {
    this.copyTodos = [... this.todos];
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
#script{
  background-color: cadetblue;
}

h2 {
  text-align: center;
  padding: 0 20px;
}

body {
  font-family: Arial, Arial, Helvetica, sans-serif;
  font-size: 1.2em;
  padding: 0;
  margin: 0;
  background-image: url('./assets/espacio.jpg');
}

#main-container {
  border: solid 1px #ccc;
  width: 700px;
  margin: 100px auto;
  background-image: url('./assets/espacio3.jpg');
}

#header {
  background-image: url('./assets/espacio.jpg');
  padding: 10px;
}

</style>
