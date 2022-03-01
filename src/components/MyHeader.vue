<template>
    <header>
        <div class="title"><h1>Boolflix</h1></div>
        <form>
            <input type="text" v-model='searchText'>
            <button type="submit" @click.prevent="$emit('search',searchText)">Ricerca</button>
        </form>
    </header>
</template>

<script>
export default {
    name:'MyHeader',
    
    data(){
        return{
            searchText:'',
        }
    }
}
</script>

<style lang="scss" scoped>
    header{
        height: 80px;
        display: flex;
        align-items: center;
        background-color: rgb(129, 129, 129);
        justify-content: space-between;
        h1{
            color: red;
            font-size: 90px;
        }
    }
</style>