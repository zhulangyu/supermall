<template>
 <div>
   <nav-bar class="home-nav"> <div slot="center">购 物 街</div></nav-bar>
   <home-swiper :banners="banners" />
   <recommend-view :recommends="recommends" />
 </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";
import HomeSwiper from "./chindcomponents/homeSwiper"
import RecommendView from "./chindcomponents/recommendviews"


import {getHomeMultidata} from "network/home"

  export default {
    name: "Home",
    components:{
      NavBar,
      HomeSwiper,
      RecommendView,
    },
    data() {
      return {
        banners:[],
        recommends:[],
        // result:null
      
        
      }
    },
    
    created() {
      getHomeMultidata().then(res => {
        // console.log(res)
        this.banners = res.data.data.banner.list;
        this.recommends = res.data.data.recommend.list;
        // this.result=res
        
      }) 
    },  
  }
</script>

<style scoped>
  .home-nav{
    background-color: var(--color-tint);
    color: #fff;
  }
</style>
