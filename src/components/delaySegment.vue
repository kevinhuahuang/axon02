<template>
  <div id="delay_segment">
    <span style="position:absolute; top:10px; left:6px; font-size:12px; font-weight:700;  color:#a1d1d0">DELAY</span>
    <span style="position:absolute; top:35px; left:6px; font-size:12px; font-weight:700; color:#a1d1d0">PAN</span>
    <delay-route class="route route1" :parent-steps=route1Steps></delay-route>
    <delay-route class="route route2" :parent-steps=route2Steps></delay-route>
    <delay-route class="route route3" :parent-steps=route3Steps></delay-route>
    <delay-route class="route route4" :parent-steps=route4Steps></delay-route>
    <delay-route class="route route5" :parent-steps=route5Steps></delay-route>
    <delay-route class="route route6" :parent-steps=route6Steps></delay-route>
    <delay-route class="route route7" :parent-steps=route7Steps></delay-route>
    <span class="border-top"></span>
    <span class="border-right"></span>
    <span class="border-left"></span>
    <span class="border-bottom"></span>
  </div>
</template>

<script>
import Slider from './public/slider'
import DelayRoute from './public/delayRoute'
export default {
  name: 'delaySegment',
  components: {DelayRoute, Slider},
  data () {
    return {
      route1Steps: 10,
      route2Steps: 70,
      route3Steps: 40,
      route4Steps: 80,
      route5Steps: 30,
      route6Steps: 20,
      route7Steps: 60
    }
  }
}
</script>

<style scoped>
  #delay_segment {
    position: absolute;
    width: 590px;
    height: 270px;
    background-color: #050d0f;
    border: 2px solid #66a2a6;
  }
  .route {
    position: absolute;
    top: 5px;
  }
  .route1 {
    left: 50px;
  }
  .route2 {
    left: 125px;
  }
  .route3 {
    left: 200px;
  }
  .route4 {
    left: 275px;
  }
  .route5 {
    left: 350px;
  }
  .route6 {
    left: 425px;
  }
  .route7 {
    left: 500px;
  }
  .border-top, .border-bottom {
    position: absolute;
    left: 10px;
    width: 570px;
    height:2px;
    background-color: #05090b;
  }
  .border-top {
    top: -2px;
  }
  .border-bottom {
    bottom: -2px;
  }
  .border-left, .border-right {
    position: absolute;
    top: 10px;
    width: 2px;
    height: 250px;
    background-color: #05090b;
  }
  .border-left {
    left: -2px;
  }
  .border-right {
    right: -2px;
  }
</style>
