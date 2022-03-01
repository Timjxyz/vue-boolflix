<template>
  <section>
       <h1 id="title">Lista Film</h1>
      <ul class="d-flex">
          <MyCard v-for="(film, index) in films" :key="index" :info='film'/>
      </ul>
  </section>
</template>

<script>
import MyCard from './partials/MyCard.vue';
export default {
    name:'FilmList',
    props:{
        'films':Array
    },
    components:{
        MyCard
    }

}
</script>

<style lang="scss" scoped>
    #title{
        text-align: center;
        color: white;
        font-size: 60px;
    }
    .d-flex{
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
    }

</style>