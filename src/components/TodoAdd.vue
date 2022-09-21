<template>
    <div id="add-container">
        <form @submit="addTodo">
            <input type="text" v-model="title">
        </form>
    </div>
</template>
<script>
    //importamos uuid 
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


//usamos uuid para obtener un id aleatorio
const newTodo = {
    id: uuid.v4(),
    title: this.title,
    completed: false
};

//regresamos a titile con string vacio. Llamamos emit para cargar una nueva tarea
this.$emit('add-todo', newTodo)
        },
    }
}
</script>
<style scoped>
    #add-container{
        padding: 10px;
        background-color: rgb(255, 247, 247);
    }
    input{
        align-items: center;
        padding: 10px;
        outline: none;
        border: solid 10px rgb(212, 182, 10);
        width: 100%;
        color: rgb(250, 11, 11);
        font-size: 20px;
    }
</style>