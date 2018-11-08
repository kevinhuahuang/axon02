<template>
  <div id="fix_segment">
    <cross class="cross_class"></cross>
    <div class="mute_div">
      <mute-button class="mute_class" parent-text="MUTE"></mute-button>
      <slider class="slider_class"></slider>
    </div>
    <div class="knob_div">
      <sync-button class="sync_left" parent-text="SYNC L">></sync-button>
      <sync-button class="sync_right" parent-text="SYNC R"></sync-button>
      <knob class="knob_l"  @onEffectDisplayChange="onEffectDisplayChange" parent-type="L_TIME"  :parent-angle=lSteps></knob>
      <knob class="knob_r"  @onEffectDisplayChange="onEffectDisplayChange" parent-type="R_TIME"  :parent-angle=rSteps></knob>
      <knob class="knob_flt"  @onEffectDisplayChange="onEffectDisplayChange" parent-type="FLT_WIDTH"  :parent-angle=fltSteps></knob>
      <fix-display class="display_l" parent-type="L TIME" :parent-value=lStepsValue></fix-display>
      <fix-display class="display_r" parent-type="R TIME" :parent-value=rStepsValue></fix-display>
      <fix-display class="display_flt" parent-type="FLT WIDTH" :parent-value=fltStepsValue></fix-display>
    </div>
    <span class="border-top"></span>
    <span class="border-right"></span>
    <span class="border-left"></span>
    <span class="border-bottom"></span>
    <span class="notice">FEEDBACK/FILTER</span>
  </div>
</template>

<script>
import Cross from './public/cross'
import Knob from './public/knob'
import Slider from './public/slider'
import MuteButton from './public/muteButton'
import SyncButton from './public/syncButton'
import FixDisplay from './public/fixDisplay'
export default {
  name: 'fixSegment',
  components: {FixDisplay, SyncButton, MuteButton, Knob, Cross, Slider},
  data () {
    return {
      lSteps: 0,
      rSteps: 0,
      fltSteps: 0,
      lStepsValue: '1/16',
      rStepsValue: '1/4',
      fltStepsValue: '1Oct'
    }
  },
  methods: {
    onEffectDisplayChange (type, value) {
      // console.log('type:' + type)
      // console.log('value:' + value)
      switch (type) {
        case 'L_TIME':
          this.lStepsValue = Math.floor(value / 270 * 100) + '/16'
          break
        case 'R_TIME':
          this.rStepsValue = Math.floor(value / 270 * 100) + '/4'
          break
        case 'FLT_WIDTH':
          this.fltStepsValue = Math.floor(value / 270 * 100) + 'Oct'
          break
        default:
          break
      }
    }
  }
}
</script>

<style scoped>
  #fix_segment {
    position: absolute;
    width: 436px;
    height: 270px;
    background-color: #05090b;
    border: 2px solid #66a2a6;
  }
  .cross_class {
    position: absolute;
    top: 41px;
    left: 25px;
  }
  .mute_div {
    position: absolute;
    left: 220px;
    top: 41px;
    width: 70px;
    height: 188px;
    background-color: #05090a;
  }
  .mute_class {
    position: absolute;
    top:0;
    left: 6px;
  }
  .slider_class {
    position: absolute;
    top: 25px;
    left: 6px;
  }
  .sync_left {
    position: absolute;
    left: -1px;
  }
  .sync_right {
    position: absolute;
    right: 7px;
  }
  .knob_div {
    position: absolute;
    top: 41px;
    right: 10px;
    width: 130px;
    height: 188px;
    background-color: #05090a;
  }
  .knob_r, .knob_l, .knob_flt {
    position: absolute;
    left: 1px;
  }
  .knob_l, .display_l{
    top: 25px;
  }
  .knob_r, .display_r{
    top: 83px;
  }
  .knob_flt, .display_flt{
    top: 140px;
  }
  .display_l,.display_r, .display_flt {
    position: absolute;
    right: -3px;
  }
  .border-top, .border-bottom {
    position: absolute;
    left: 10px;
    width: 416px;
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
  .notice {
    position: absolute;
    left: 60px;
    bottom: 15px;
    font-size: 12px;
    font-weight: bold;
    color: #a1d1d0
  }
</style>
