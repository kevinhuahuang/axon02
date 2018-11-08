<template>
  <div class="knob_display">
    <effect-display class="display display1" parent-type="PITCH" :parent-value="pitchValue"></effect-display>
    <effect-display class="display display2" parent-type="THRESHOLD" :parent-value="thresholdValue"></effect-display>
    <effect-display class="display display3" parent-type="DISTORTION" :parent-value="distortionValue"></effect-display>
    <effect-display class="display display4" parent-type="NOISE" :parent-value="noiseValue"></effect-display>
    <knob class="knob_class knob1" @onEffectDisplayChange="onEffectDisplayChange" parent-type="PITCH"  :parent-angle=pitchStep></knob>
    <knob class="knob_class knob2" @onEffectDisplayChange="onEffectDisplayChange" parent-type="THRESHOLD"  :parent-angle=thresholdStep></knob>
    <knob class="knob_class knob3" @onEffectDisplayChange="onEffectDisplayChange" parent-type="DISTORTION"  :parent-angle=distortionStep></knob>
    <knob class="knob_class knob4" @onEffectDisplayChange="onEffectDisplayChange" parent-type="NOISE" :parent-angle=noiseStep></knob>
  </div>
</template>

<script>
import Knob from './knob'
import EffectDisplay from './effectDisplay'
export default {
  name: 'knobDisplay',
  components: {EffectDisplay, Knob},
  data () {
    return {
      pitchValue: 'C0',
      thresholdValue: '3',
      distortionValue: '7%',
      noiseValue: '11%',
      pitchStep: 0,
      thresholdStep: 10,
      distortionStep: 20,
      noiseStep: 30
    }
  },
  mounted: function () {
  },
  methods: {
    onEffectDisplayChange (type, value) {
      // console.log('type:' + type)
      // console.log('value:' + value)
      switch (type) {
        case 'PITCH':
          this.pitchValue = 'C' + Math.floor(value / 270 * 100)
          break
        case 'THRESHOLD':
          this.thresholdValue = Math.floor(value / 270 * 100) + ''
          break
        case 'DISTORTION':
          this.distortionValue = Math.floor(value / 270 * 100) + '%'
          break
        case 'NOISE':
          this.noiseValue = Math.floor(value / 270 * 100) + '%'
          break
        default:
          break
      }
    }
  },
  props: {
    parentPitchValue: {
      type: String,
      default: 'C3'
    },
    parenThresholdValue: {
      type: String,
      default: '0'
    },
    parenDistortionValue: {
      type: String,
      default: '51%'
    },
    parenNoiseValue: {
      type: String,
      default: '91%'
    }
  },
  watch: {
    parentPitchValue (curV, oldV) {
      this.pitchValue = curV
    },
    parenThresholdValue (curV, oldV) {
      this.thresholdValue = curV
    },
    parenDistortionValue (curV, oldV) {
      this.distortionValue = curV
    },
    parenNoiseValue (curV, oldV) {
      this.noiseValue = curV
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
  }
  .display {
    position: absolute;
    left: 1px;
  }
  .knob_class {
    position: absolute;
    right: 1px;
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
