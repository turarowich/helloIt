<template>
    <div class="main-course">
        <transition name="fade">
        <slideModal  v-if="modal" 
        @close="modal=false" 
        :name="courseData.name"
        :desc="courseData.description"
        :t="courseData.telegram"
        :p="courseData.phone"
        :y="courseData.youtube"
        :i="courseData.instagram"
        />
        </transition>
        <div class="wrapper">
            <div class="border">
                <div class="border-wrapper">
                    <div class="content">
                        <div class="title">
                           {{courseData.name}}
                        </div>
                        <ul>
                            <li @click="modal=true">
                                <img @click="modal=true" src="@/assets/imgs/info.png" alt="">
                                <span @click="modal=true" >Информация о курсе</span>
                            </li>
                             <li>
                                <img src="@/assets/imgs/vidoe.png" alt="">
                                <span >{{courseData.video_count}} видео сабак</span>
                            </li>
                             <li>
                                <img src="@/assets/imgs/testc.png" alt="">
                                <span>{{courseData.test_count}} Тест</span>
                            </li>
                        </ul>
                    </div>

                    <img width="331" :src="courseData.icon" alt="">
                </div>
            </div>
            <div class="rectangle">
                <div class="rectangle-wrapper">
                    <div class="rectangle-container">
                        <div class="card">
                            <img src="@/assets/imgs/people.png" alt="">
                            <span>{{courseData.views}}</span>
                        </div>
                        <div class="card">
                            <img src="@/assets/imgs/star.png" alt="">
                            <span>{{courseData.rating}}</span>
                        </div>
                        <div class="card">
                            <img src="@/assets/imgs/heart.png" alt="">
                            <span>{{courseData.likes}}</span>
                        </div>
                    </div>
                </div>
            </div>

            <div class="views">
                <div class="views-wrapper">
                    <div class="views-container">
                        <div class="links">
                            <nuxt-link active-class="active"  :to="`/course/${routeid}/video`" class="deafult">Видео сабактар</nuxt-link>
                            <nuxt-link active-class="active" :to="`/course/${routeid}/tests`" class="deafult">Тесттер</nuxt-link>
                            <nuxt-link active-class="active" to="#" class="deafult">Кошумча материалдар</nuxt-link>
                        </div>

                        <div class="view">
                            <nuxt-child
                             :data="{
                             count:courseData.video_count,
                             icon:courseData.icon,
                             name:courseData.name,
                             desc:courseData.description,
                             test_count:courseData.test_count}" 
                             />
                        </div>
                    </div>
                </div>
            </div>
        </div>


        <div class="like-comment">
            <img src="@/assets/imgs/like.png" alt="">
            <img src="@/assets/imgs/comment.png" alt="">
        </div>


    </div>
</template>

<script>
export default {
    data:()=>({
        courseData:{},
        modal:false
    }),
    mounted(){
        this.$store.dispatch('header/setColors',{
            bg:'#fff',
            burger:'#0B0D34',
            nav:'#0B0D34'
        })
        this.$axios.get('http://176.126.164.190:8000/api/bilimcourses/'+this.$route.params.id)
            .then(data=>{
                this.courseData = data.data
            })
        
            



        
    },

    computed:{
        routeid(){
            return this.$route.params.id
        }
    }
}
</script>

<style scoped>

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}

.like-comment{
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    gap: 20px;

    position: absolute;
    top:600px;
    right:70px;
}
.views{
    margin-top:40px;
    width: 100%;

}
.views-wrapper{
    width: 80%;
    margin: 0 auto;

}
.views-container{
    width: 100%;
    margin: 0 90px;
}
.views-container .links{
    display: flex;
    align-items: center;
    gap :35px;
}
.views-container .links a{
    font-family: Roboto;
font-style: normal;
font-weight: normal;
font-size: 24px;
line-height: 28px;
text-decoration: none;
/* Secondary */

}


.view{
    height: 420px;
    width: 100%;
    margin: 40px 0 180px 0;
    padding: 30px 0;
}




.rectangle{
    min-height: 64px;
    width: 100%;
    position: absolute;
    background: #0B0D34;
    top:400px;
    left:0;
    display: flex;
    align-items: center;
}
.rectangle-wrapper{
    width: 80%;
    margin: 0 auto;
    display: flex;
    align-items: center;
}
.rectangle-container{
    margin: 0 200px;
    display: flex;
    gap :73px;
    align-items: center;
}
.rectangle-container .card{
    display: flex;
    align-items: center;
    gap:20px
}
.rectangle-container .card span{
   font-family: Roboto;
font-style: normal;
font-weight: normal;
font-size: 20px;
line-height: 30px;
/* identical to box height, or 150% */


color: #FFFFFF;

}


.main-course{
    width: 100%;
}
.wrapper{
    width: 80%;
    margin: 0 auto;
}

.border{
    width: 100%;
    border: 1px solid #E0E7EA;
    border-radius: 14px;
    padding: 0 200px;
    min-height: 372px;
}

.title{
    
font-family: Roboto;
font-style: normal;
font-weight: 500;
font-size: 24px;
line-height: 30px;
/* identical to box height, or 125% */


/* BACKGROUND */

color: #0B0D34;

}
.border-wrapper{
    display: flex;
    justify-content: space-between;
    gap :100px;
}
.border-wrapper > img{
    margin-top: 20px;
}
li{
    list-style: none;
    margin: 14px 0 0 0;
    display: flex;
    gap :12px;
    align-items: center;
}
li span{
    font-family: Roboto;
font-style: normal;
font-weight: normal;
font-size: 18px;
line-height: 30px;
/* identical to box height, or 167% */


/* Secondary */

color: #7E7E7E;
}
li img{
    max-height: 20px;
    max-width: 20px;
}
ul{
    margin: 20px 0 0 0;
}

.content{
    margin-top: 57px;
}

.deafult{
    color:  #7E7E7E;
}
.active{
color: #21A95D;
}


@media screen and (max-width:1161px) {
    .like-comment{
        right:10px
    }
}

@media screen and (max-width:925px) {
    .border{
        padding: 0 30px;
    }
    .rectangle-container{
        margin: 0 100px;
    }
}

@media screen and (max-width:795px) {
    .like-comment{
        top:370px
    }
    
}


@media screen and (max-width:857px) {
    .links{
        overflow-x: scroll;
    }
    .links a {
        white-space: nowrap;
    }
    .views-container{
        margin: 0 auto;
    }

}

/* width */
.links::-webkit-scrollbar {
    display: none;
}

/* Track */
.links::-webkit-scrollbar-track {
    display: none;
}

/* Handle */
.links::-webkit-scrollbar-thumb {
  display: none;
}

@media screen and (max-width:530px) {
    .rectangle-wrapper{
        width: 95%;
    }
    .rectangle-container{
        margin: 0 auto;
        gap:30px;
    }
}

@media screen and (max-width:735px) {
    .border-wrapper{
        flex-direction: column;
        gap :30px
    }
    .rectangle{
        top:710px
    }
    .like-comment{
        top:684px
    }
    .views{
        margin-top: 88px;
    }
}

@media screen and (max-width:670px) {
    .border-wrapper > img{
        width: 70%;
        margin: 0 auto;
    }
    .rectangle{
        top:570px
    }
    .like-comment{
        top:554px;
    }
}

@media screen and (max-width:512px) {
    .rectangle{
        top:500px ;
    }
    .content{
        margin-top: 30px;
    }
    
}

@media screen and (max-width:450px) {
    .like-comment{
        top:483px
    }
    .views{
        margin-top: 110px;
    }
}
@media screen and (max-width:400px) {
    .wrapper{
        width: 100%;
    }
}
</style>

