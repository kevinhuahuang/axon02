<template>
  <div class="effect_segment">
    <knob-display class="knob_display"></knob-display>
    <effect-cross class="fm_cross"></effect-cross>
    <span class="fm_notice">FM</span>
    <effect-cross class="timbre_cross"></effect-cross>
    <span class="timbre_notice">TIMBRE</span>
    <env-div class="env_div"></env-div>
    <knob-right-display class="right_knob_display"></knob-right-display>
    <span class="border-top"></span>
    <span class="border-right"></span>
    <span class="border-left"></span>
    <span class="border-bottom"></span>
  </div>
</template>

<script>
import KnobDisplay from './public/knobDisplay'
import EffectCross from './public/effectCross'
import KnobRightDisplay from './public/knobRightDisplay'
import EnvDiv from './public/envDiv'
export default {
  name: 'effectSegment',
  components: {EnvDiv, KnobRightDisplay, EffectCross, KnobDisplay}
}
</script>

<style scoped>
  * {
    user-select: none;
  }
  .effect_segment {
    position: absolute;
    width: 590px;
    height: 270px;
    background-color: #05090b;
    border: 2px solid #66a2a6;
  }
  .knob_display {
    position: absolute;
    left: 2px;
    top: 5px;
  }
  .fm_cross {
    position: absolute;
    left: 155px;
    top: 5px;
  }
  .fm_notice {
    position: absolute;
    left: 165px;
    top: 5px;
    color: #a5d8d8;
    font-size: 12px;
    font-weight: bold;
  }
  .timbre_cross {
    position: absolute;
    left: 305px;
    top: 5px;
  }
  .timbre_notice {
    position: absolute;
    left: 315px;
    top: 10px;
    color: #a5d8d8;
    font-size: 12px;
    font-weight: bold;
  }
  .env_div {
    position: absolute;
    left: 155px;
    top: 130px;
  }
  .right_knob_display {
    position: absolute;
    left: 452px;
    top: 5px;
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
