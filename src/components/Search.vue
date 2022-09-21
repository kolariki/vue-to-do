

<template>
    <div id="search-container">
        <input type="text" v-model="query" v-on:input="$emit('query-change', query)">
    </div>
</template>
<script>
//con el v-model"query" tomamos lo que se escribe en el search y 
//rellenamos el data del return y con el v-on:input-emit enviamos el request y filtramos los datos
// cuando ingreso informacion y no cuando cambia el estado, el cuall llama al query change y mande el query

export default {
    name: 'Search',
    data(){
        return {
            query: ''
        }
    }
}

</script>

<style>
    #search-container{
        width: 500px;
        margin: 0 auto;
        background-color: rgb(236, 226, 226);
        padding: auto;
    }

    input{
        padding: 10px;
        width: 100%;
        outline: none;
        background-color: rgb(218, 214, 214);
        color: rgb(189, 21, 15);
        font-size: 20px;
        border: solid 10px rgb(17, 17, 17);
    }
  
</style>