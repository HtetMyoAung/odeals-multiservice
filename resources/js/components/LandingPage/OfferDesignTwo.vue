<template>
  <section class="offer-two">
    <div class="container">
      <h3>Grab Deals and Special Offers</h3>
      <div  class="swiper-container offerSlider">
        <div class="swiper-wrapper">
            <div  class="swiper-slide" v-for="(data,index) in discountservice" :key="index">
                <div class="offer-box">
                    <div class="offer-info">
                        <div class="offer-title">
                            <span class="text-primary sub-title">{{__('messages.best_deal_month')}}</span>
                        <router-link :to="{name: 'service-detail',params: { service_id: data.id }}" class="main-title"><h3 class="text">{{data.name}}</h3></router-link>
                        </div>
                        <div class="offer-text">
                            <b>{{data.discount}}% {{__('messages.off')}}</b> {{__('messages.on_all_item')}}
                        </div>
                    </div>
                    <div class="offer-image">
                        <img :src="data.attchments[0] ? data.attchments[0]: baseUrl+'/images/default.png'" >
                        <div class="offer-disc">
                            <span class="disc-name">From {{data.price_format}}</span>
                        </div>
                    </div>                               
                </div>
            </div>
        </div>
        <div class="swiper-pagination"></div>
    </div>
</div>
</section>
</template>
<style scoped>
.our-offer{
padding:100px 0;
}
</style>
<script>
import { mapGetters } from "vuex"
import Swiper, { Navigation, Pagination, Parallax, Autoplay } from 'swiper'
Swiper.use([Navigation, Pagination, Parallax, Autoplay])
export default {
name:'Offer',
data(){
    return{
        baseUrl:window.baseUrl
    }
},
mounted(){
    new Swiper(".offerSlider", {
        autoplay:{delay: 2000},
        loop: true,
        spaceBetween: 30,
        observer: true,  
        observeParents: true,
        slidesPerView: "auto",
        centeredSlides: true,
        loopFillGroupWithBlank: true,
        pagination: {
            el: ".swiper-pagination",
            clickable: true,
        },
        // breakpoints: {
        //     320: { slidesPerView: 1 },
        //     768: { slidesPerView: 2},
        //     1199: { slidesPerView: 2 },
        //     1400: { slidesPerView: 2 },
        //     1500: { slidesPerView: 2 },
        //     1920: { slidesPerView: 2},
        // },
    });
},
computed: {
    ...mapGetters(["discountservice"]),
},

}
</script>
