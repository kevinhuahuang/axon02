<template>
  <div class="delay_route">
    <strip-slider class="slider_delay"></strip-slider>
    <strip-slider class="slider_pan"></strip-slider>
    <square-button class="button_m" text="M"></square-button>
    <square-button class="button_s" text="S"></square-button>
    <slider class="slider_gain" @onSliderStepChange="onSliderStepChange" :parent-steps=parentSteps></slider>
    <span class="data_value" v-text="dataValue"></span>
  </div>
</template>

<script>
import StripSlider from './stripSlider'
import SquareButton from './squareButton'
import Slider from './slider'
export default {
  name: 'delayRoute',
  components: {Slider, SquareButton, StripSlider},
  data () {
    return {
      steps: 0,
      dataValue: 0
    }
  },
  mounted: function () {
    this.steps = this.parentSteps
    this.getDataValue(this.steps)
  },
  methods: {
    onSliderStepChange: function (steps) {
      this.getDataValue(steps)
    },
    getDataValue: function (steps) {
      this.dataValue = Math.floor((steps / 145) * 100) + ''
      this.dataValue = this.dataValue.length > 1 ? this.dataValue : '0' + this.dataValue
    }
  },
  props: {
    parentDataValue: {
      type: String,
      default: '00'
    },
    parentSteps: {
      type: Number,
      default: 0
    }
  },
  watch: {
    parentDataValue (curV, oldV) {
      this.dataValue = curV
    }
  }
}
</script>

<style scoped>
  .delay_route {
    position: absolute;
    width: 60px;
    height: 260px;
    background: #05090b
  }
  .slider_delay {
    top: 2px;
    left: 4px;
  }
  .slider_pan {
    top: 27px;
    left: 4px;
  }
  .button_m {
    top: 52px;
    left: 8px;
  }
  .button_s {
    top: 52px;
    right: 8px;
  }
  .slider_gain {
    left: 4px;
    bottom: 22px;
  }
  .data_value {
    position: absolute;
    left: 22px;
    bottom: 2px;
    font-family: Arial, serif;
    font-weight: 100;  /* <500 not work*/
    font-stretch: ultra-condensed; /* not work*/
    color: #a1d1d0;
  }
</style>
