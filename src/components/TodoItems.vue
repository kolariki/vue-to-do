<template>
    <div class="todo" v-bind:class="{completed: todo.completed}">
        <div class="todo-body" >
            <input type="checkbox" 
            v-bind:checked="checked"
            v-on:change="checkTodo">
            {{todo.title}}
        </div>

        <div class="todo-actions">
            <button @click="$emit('delete-todo', todo.id)"> Eliminar </button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props: ['todo'],
    methods: {
        checkTodo(){
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style>
.todo{
        border-bottom: solid 1px rgb(133, 8, 8);
        padding: 10px;
        background-color: rgb(209, 206, 17);
    }
.todo:not( .completed) :hover{
    background-color: rgb(102, 98, 98);
}
.completed{
    color: rgb(216, 13, 13);
    text-decoration: line-through;
}
.completed .todo-body{
    text-decoration: line-through;
}
.todo-body, .todo-actions{
    display:inline-block;
    vertical-align: top;
    background-color: rgb(204, 201, 50);
}
.todo-body{
    width: 85%;
    
}
.todo-actions{
    padding: 0 10px;
    width: 10%;
}
button{
    border: none;
    border-radius: 10px;
    padding: 10px;
    background-color: rgb(18, 82, 221);
    color: black;
}
button:hover{
    background-color: #f00606;
    color: white;
}
</style>