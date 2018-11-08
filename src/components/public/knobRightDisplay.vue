<template>
  <div class="knob_display">
    <effect-display class="display display1" parent-type="FM SEND" :parent-value=fmSendValue></effect-display>
    <effect-display class="display display2" parent-type="FM RCV" :parent-value=frRcvValue></effect-display>
    <effect-display class="display display3" parent-type="AM SEND" :parent-value=amSendValue></effect-display>
    <effect-display class="display display4" parent-type="AM RCV" :parent-value=amRcvValue></effect-display>
    <knob class="knob_class knob1" @onEffectDisplayChange="onEffectDisplayChange" parent-type="FM_SEND"  :parent-angle=fmSend></knob>
    <knob class="knob_class knob2" @onEffectDisplayChange="onEffectDisplayChange" parent-type="FR_RCV"  :parent-angle=frRcv></knob>
    <knob class="knob_class knob3" @onEffectDisplayChange="onEffectDisplayChange" parent-type="AM_SEND"  :parent-angle=amSend></knob>
    <knob class="knob_class knob4" @onEffectDisplayChange="onEffectDisplayChange" parent-type="AM_RCV"  :parent-angle=amRcv></knob>
  </div>
</template>

<script>
import Knob from './knob'
import EffectDisplay from './effectDisplay'
export default {
  name: 'knobRightDisplay',
  components: {EffectDisplay, Knob},
  data () {
    return {
      fmSend: 0,
      frRcv: 0,
      amSend: 0,
      amRcv: 0,
      fmSendValue: '0',
      frRcvValue: '3',
      amSendValue: '7',
      amRcvValue: '11'
    }
  },
  mounted: function () {
  },
  methods: {
    onEffectDisplayChange (type, value) {
      // console.log('type:' + type)
      // console.log('value:' + value)
      switch (type) {
        case 'FM_SEND':
          this.fmSendValue = Math.floor(value / 270 * 100) + '%'
          break
        case 'FR_RCV':
          this.frRcvValue = Math.floor(value / 270 * 100) + '%'
          break
        case 'AM_SEND':
          this.amSendValue = Math.floor(value / 270 * 100) + '%'
          break
        case 'AM_RCV':
          this.amRcvValue = Math.floor(value / 270 * 100) + '%'
          break
        default:
          break
      }
    }
  }
}
</script>

<style scoped>
  * {
    user-select: none;
  }
  .knob_display {
    position: absolute;
    width:  140px;
    height: 250px;
    background-color: #05090b;
  }
  .display {
    position: absolute;
    right: 2px;
  }
  .knob_class {
    position: absolute;
    left: 1px;
  }
  .display1, .knob1 {
    top: 0;
  }
  .display2, .knob2 {
    top: 65px;
  }
  .display3, .knob3 {
    top: 130px;
  }
  .display4, .knob4 {
    top: 195px;
  }
</style>
