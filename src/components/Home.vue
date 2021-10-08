<template>
  <div class="home">
      <Navbar class="navbar"/>
      <img class="poster" :src="poster" alt="">
      <div class="container">
        <p class="marvel">{{ copy.marvel }}</p>
        <p class="title">{{ copy.title }}</p>
        <p class="description">{{ copy.description }}</p>
        <div class="buttons">
          <button @click="showSchedule = !showSchedule" class="buy">{{ copy.buy }}</button>
          <button @click="showTrailer = !showTrailer" class="watch">{{ copy.watch }}</button>
          <div class="release">{{ copy.release }}</div>
        </div>
      </div>
      <Schedule class="schedule" :class="{'is-active': showSchedule}"
        :showSchedule="showSchedule"
        @closeSchedule="closeSchedule"
      />
      <Trailer class="trailer" :class="{'is-active': showTrailer}"
        :showTrailer="showTrailer"
        @closeTrailer="closeTrailer"
      />
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'
import Schedule from '@/components/Schedule.vue'
import Trailer from '@/components/Trailer.vue'
import copy from '@/copy.js'
export default {
  name: 'Home',
  components: {
    Navbar,
    Schedule,
    Trailer
  },
  data() {
    return {
      copy: copy,
      poster: require('@/assets/poster.png'), 
      showSchedule: false,
      showTrailer: false
    }
  },
  methods:{
    closeSchedule(){
      this.showSchedule = false
    },
    closeTrailer(){
      this.showTrailer = false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .home{
    position: relative;
    height: 100vh;
  }
  .navbar{
    position: absolute;
    top: 0;
    z-index: 99;
  }
  .poster{
    position: relative;
    height: 50%;
    width: 100%;
  }
  .container{
    position: relative;
    height: fit-content;
    padding: 24px
  }
  .marvel{
    font-size: 14px;
    color: #C2C2C2;
    margin-bottom: 7px !important;
  }
  .title{
    font-size: 23px;
    color: #000000;
    margin-bottom: 9px !important;
  }
  .description{
    font-size: 14px;
    margin-bottom: 12px !important;
  }
  .buttons{
    display: flex;
  }
  .buy{
    width: 50%;
    height: 58px;
    background: #FFFFFF;
    color: #0286FF;
    border: 1px solid #0286FF;
    box-sizing: border-box;
    border-radius: 36px;
    font-size: 20px;
  }
  .watch{
    background: #FFFFFF;
    border: 0;
    width: 50%;
    height: 58px;
    font-size: 18px;
    color: #000000;
  }
  .release{
    position: absolute;
    top: -16px;
    left: 24px;
    padding: 4px 8px;
    display: inline-block;
    font-size: 15px;
    background: linear-gradient(90deg, #69FF9C 0%, #5DD686 100%);
    border-radius: 4px;
  }
  .schedule, .trailer{
    visibility: hidden;
    height: 0%;
    transition: all 0.3s ease;
  }
  .schedule.is-active, .trailer.is-active{
    visibility: visible;
    height: 94vh;
  }
</style>
