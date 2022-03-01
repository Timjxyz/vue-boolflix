<template>
  <section>
      <h1 id="title">----Lista serie----</h1>
      <ul class="d-flex">
          <MyCard v-for="(serie, index) in series" :key="index" :info='serie'/>
      </ul>
  </section>
</template>

<script>
import MyCard from './partials/MyCard.vue';
export default {
    name:'SerieList',
    props:{
        'series':Array
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
        padding: 30px;
    }
    .d-flex{
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
    }
</style>