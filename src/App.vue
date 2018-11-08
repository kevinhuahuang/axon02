<template>
  <div id="app">
    <div class="container">
      <div class="content">
        <navigator-header style="width:1060px"></navigator-header>
        <div style="height:60px;"></div>
        <div class="app_div">
          <header-segment class="header_segment"></header-segment>
          <network-segment class="network_segment"></network-segment>
          <effect-segment class="effect_segment"></effect-segment>
          <fix-segment class="fix_segment"></fix-segment>
          <delay-segment class="delay_segment"></delay-segment>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import HeaderSegment from './components/headerSegment'
import PublicTest from './components/publicTest'
import NetworkSegment from './components/networkSegment'
import FixSegment from './components/fixSegment'
import DelaySegment from './components/delaySegment'
import EffectSegment from './components/effectSegment'
import NavigatorHeader from './components/public/NavigatorHeader'

export default {
  name: 'App',
  components: {
    NavigatorHeader,
    EffectSegment,
    DelaySegment,
    FixSegment,
    NetworkSegment,
    PublicTest,
    HeaderSegment
  },
  data () {
    return {
      mainLinkArray: [['主页', '../guide'], ['简历', '../resume']],
      linkArray: [['网页应用', '../dp7'], ['商城', '../millet'], ['股票', '../start_page'], ['其它', '../others']]
    }
  },
  methods: {
    returnHome: function () {
      window.location.href = '../home'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/

}
  .content {
    margin-left: auto;
    margin-right: auto;
    left: 0;
    right: 0;
    width: 1060px;
  }
  .app_div {
    position: absolute;
    background-color: #05090b;
    width: 1060px;
    height: 660px;
  }
  .header_segment {
    position: absolute;
    margin-top: 10px;
  }
  .network_segment, .effect_segment {
    position: absolute;
    top: 80px;
  }
  .network_segment, .fix_segment {
    left: 10px;
  }
  .effect_segment, .delay_segment {
    left: 460px;
  }
  .fix_segment, .delay_segment {
    position: absolute;
    top: 370px;
  }
</style>
