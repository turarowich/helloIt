<template>
<div class="main">
       <div v-for="i of 5" :key="i" class="video">
           <img width="138" height="138" style="border-radius:5px;" src="@/assets/imgs/news/news.png" />
            <div class="content">
                <div class="title">Кореядагы эң көп стипендия! Айына $800. KGSP ге кантип тапшыруу</div>
                <div class="des">Кореяда кантип айына миллион вон алып окууса болору тууралуу Жумаева Насиба эжем менен</div>
                <div class="more">Читать полностью</div>
            </div>  
       </div>
    </div>
</template>


<style lang="scss" scoped>
@import '@/assets/styles/main.scss';
.main{
    width: 100%;
    height: 420px;
    overflow-y: scroll;

}
.video{
    width: 100%;
    display:flex;
    gap:30px;
    border-bottom: 1px solid  #E0E7EA;;
    border-top: 1px solid  #E0E7EA;;
    padding: 30px 0 30px 0;
}
/* width */
.main::-webkit-scrollbar {
  width: 10px;
  border-radius: 10px;
}

/* Track */
.main::-webkit-scrollbar-track {
  background: #f1f1f1;
}
.more{
    color:$gr;
    @include h5;
    margin: 15px 0 0 0;
}
/* Handle */
.main::-webkit-scrollbar-thumb {
  background: #0B0D34;
}

.des{
    font-family: Roboto;
font-style: normal;
font-weight: normal;
font-size: 18px;
line-height: 26px;
/* or 144% */


/* Secondary */

color: #7E7E7E;
}

.title{
    font-family: Roboto;
font-style: normal;
font-weight: 500;
font-size: 20px;
line-height: 26px;
/* or 130% */


/* BACKGROUND */
margin: 0 0 10px 0;
color: #0B0D34;
}

@media screen and (max-width:620px) {
  .video{
    flex-direction: column;
  }
  img{
    width: 100%;
    height: 200px;
  }
  .video iframe{
    width: 100%;
    height: 170px;
  }
}
</style>