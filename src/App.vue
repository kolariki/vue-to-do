<template>
  <div>
  <div id="header">
    <h5> Search </h5>
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

    //añadimos el nuevo todo con push y se replica con this.copyTodos
    addTodo(todo){
            this.todos.push(todo);
            this.copyTodos = [... this.todos];
        },

        //definimos la funcion del query
        //validamos el query con el IF. Si es "" muestra todos los TO DO.
        //sino el const temp filtra y regresa todo lo que el query indique.
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

  //se ejecuta cuando carga la app y tiene todos los datos de copyTodos
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
  color: rgb(247, 14, 14);
}

body {
  font-family: Arial, Arial, Helvetica, sans-serif;
  font-size: 1.2em;
  padding: 0;
  margin: 0;
  background-image: url('./assets/gif5.gif');
}

#main-container {
  border: solid 10px rgba(36, 28, 28, 0.541);
  width: 900px;
  margin: 80px auto;
  background-image: url('./assets/gif6.gif');
}

#header {
  background-image: url('./assets/gif6.gif');
  padding: 10px;
}
h5{
  text-align: center;
  font-size: 25px;
  color: rgb(11, 153, 172);
}

</style>
