<template>
    <div id="search-container">
        <input type="text" v-model="query" v-on:input="$emit('query-change', query)">
    </div>
</template>

<script>
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
        width: 660px;
        margin: 0 auto;
        background-color: rgb(37, 33, 33);
    }

    input{
        padding: 10px;
        width: 100%;
        outline: none;
        background-color: rgb(41, 39, 39);
        color: rgb(189, 21, 15);
        font-size: 20px;
        border: solid 10px rgb(5, 71, 156);
    }
</style>