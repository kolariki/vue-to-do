<template>
    <div id="add-container">
        <form @submit="addTodo">
            <input type="text" v-model="title">
        </form>
    </div>
</template>
<script>
import {uuid} from 'vue-uuid'
export default {
    name: 'TodoAdd',
    data(){
return{
    title: ''
}
    },
    methods:{
        addTodo(e){
e.preventDefault();

const newTodo = {
    id: uuid.v4(),
    title: this.title,
    completed: false
};

this.title = '';
this.$emit('add-todo', newTodo)
        },
    }
}
</script>
<style scoped>
    #add-container{
        padding: 10px;
        background-color: rgb(204, 201, 50);
    }
    input{
        align-items: center;
        padding: 10px;
        outline: none;
        border: solid 1px #ccc;
        width: 100%;
        background-color: rgb(126, 29, 218);
    color: black;
    }
</style>