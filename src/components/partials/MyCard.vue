<template>
    <li>
        <div class="flip-card">
            <div class="container flip-card-inner">
                <div class="container-img flip-card-front">
                    <!-- Immagine della card -->
                    <img v-if="info.poster_path" :src="`https://image.tmdb.org/t/p/w342${info.poster_path}`" alt="">
                    <img v-else :src="require('../../assets/netflix.jpg')" alt="">

                </div>
            
                <div class="container-text flip-card-back">
                    <div class="translte-title">{{getTitle()}}</div>
                    <div class="og-title">{{info.original_title ? info.original_title : info.original_name}}</div>
                    <div>
                        <img v-if="language.includes(info.original_language)" :src="require('../../assets/flags/' + info.original_language + '.png')" alt="">
                        <span v-else> {{info.original_language}}</span>
                    </div>

                    <div>
                        <i v-for="i in 5" :key="i" class="fa-star" :class="(i < getStar) ? 'fa-solid' : 'fa-regular' "></i>
                        {{info.vote_averange}}
                    </div>

                </div>


            </div>

        </div>
        
    </li>
</template>

<script>
export default {
    name:'MyCard',
    props:{
        'info':Object
    },
    data(){
        return{
            language:['en','it'],
        }
    },
    computed:{
        getStar(){
            return Math.ceil(this.info.vote_average / 2);
        }
    },
    methods:{
        getTitle(){
            if(this.info.title){
                return this.info.title;
            }else{
                return this.info.name;
            }
        }
    }

}
</script>

<style lang="scss" scoped>
    li{
        width: calc(100% / 5);
        list-style: none;
        display: flex;
        justify-content: space-around;
       
    
        .container{
            position: relative;
        
            img{
                width:300px;
                height: 400px;
                object-fit: cover;
            }
            .container-text{
        
                img{
                    width: 40px;
                    height: 20px;
                    object-fit: cover;
                }

            }
        
        }
    }

    .flip-card {
        background-color: transparent;
        width: 300px;
        height: 400px;
    }

    .flip-card-inner {
        position: relative;
        width: 100%;
        height: 100%;
        text-align: center;
        transition: transform 1s;
        transform-style: preserve-3d;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    }

    .flip-card:hover .flip-card-inner {
        transform: rotateY(180deg);
    }

    .flip-card-front, .flip-card-back {
        position: absolute;
        width: 100%;
        height: 100%;
        backface-visibility: hidden;
    }

   
    .flip-card-back {
        background-color: #000;
        color: white;
        transform: rotateY(180deg);
    }
  
</style>