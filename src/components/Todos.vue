<template>
    <div id="main">
        <div v-bind:key="todo.id" v-for="todo in todoslist">
           
            <TodoItems v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)" />
        </div>
    </div>
</template>
<script>
    //con v-bind nos permite atachear todo.id
    //con v-for recorremos todo y todoslist como un for
    
import TodoItems from './TodoItems';
export default {
    name: "Todos",
    props: ["todoslist"],
    components: { TodoItems }
}
</script>

<style>
#main {
    background-color: rgb(22, 144, 192);
}
</style>