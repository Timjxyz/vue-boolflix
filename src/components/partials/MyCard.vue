<template>
    <li>
        <div class="container">
            <div class="container-img">
                <!-- Immagine della card -->
                <img v-if="info.poster_path" :src="`https://image.tmdb.org/t/p/w342${info.poster_path}`" alt="">
                <img v-else :src="require('../../assets/netflix.jpg')" alt="">

            </div>
        
            <div class="container-text">
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
        &:hover .container-text{
            display: block;
        }
        &:hover .container-img{       
            display: none;     
        }
        
        .container{
            position: relative;
            
            img{
                width:300px;
                height: 400px;
                object-fit: cover;
            }
            .container-text{
                display: none;
                width: 200px;
                text-align: center;
                color:#fff;
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%,-50%);
               
                .translte-title{
                    margin-bottom: 20px;
                }
                .og-title{
                    margin-bottom: 20px;
                }

                img{
                    width: 40px;
                    height: 20px;
                    object-fit: cover;
                }

            }
           
        }
    }
  
</style>