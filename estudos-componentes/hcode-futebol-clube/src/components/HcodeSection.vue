<template>
  <div>

    <div class="container">
      
      <div class="row mt-5">
        <h3>Você está vendo as noticias do {{ championship }}</h3>
      </div>
    
    </div>

    <transition name="fade-view" mode="out-in">
      <router-view></router-view>
    </transition>
    <!-- <component v-bind:is="currentComponent"></component> -->

    <div class="container">
      <div class="row my-club mt-5">

        <div class="col-6">
          <h2>Seu clube é {{ myClub }}</h2>
        </div>
        <div class="col-6"></div>
          <HcodeInput />
      </div>
    </div>

  </div>
</template>

<script>
// import HcodeSectionBanner from './HcodeSectionBanner.vue'
import HcodeInput from './HcodeInput.vue'
// import { mapState } from 'vuex' //importacao para uso de State
import { mapGetters } from 'vuex' //importacao para uso de Getters

export default {
  components: {
    HcodeInput,
    // HcodeSectionBanner,
    
    //usando async component para deixar a pagina mais leve
    // HcodeSectionNews: () => import('./HcodeSectionNews.vue')
  },
  data: function(){
    return {
      
    }
  },
  props: {
    currentComponent: String
  },
  computed:{
    ...mapGetters({
      championship: 'getChampionship',
      myClub: 'getClubName'
    })

    // código para uso de State
    // ...mapState(['championship']),
    // ...mapState({
    //   myClub: 'clubName'
    // })
  }
}

</script>

<style scoped>
.fade-view-enter, .fade-view-leave-to {
  opacity: 0;
}
.fade-view-enter-active, .fade-view-leave-active {
  transition: opacity .2s ease-in-out;
}
</style>