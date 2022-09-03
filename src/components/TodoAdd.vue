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
        border: solid 10px rgb(218, 19, 19);
        width: 100%;
        color: rgb(177, 13, 13);
        font-size: 20px;
    }
</style>