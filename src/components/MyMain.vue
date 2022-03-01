<template>
  <main>
      <FilmList :films='films'/>
      <SeriesList :series='series'/>


  </main>
</template>

<script>
import FilmList from './FilmList.vue'
import SeriesList from './SeriesList.vue'
export default {
    name:'MyMain',
    props:{
        'films':Array,
        'series':Array
    },
    components:{
        FilmList,
        SeriesList
    }
}
</script>

<style>
main{
    background-color: #000;
}

</style>