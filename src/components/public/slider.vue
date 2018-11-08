<template>
  <div id="slider-div" class="slider-div" @mousemove="onMouseMove" @mouseleave="onMouseLeave" @mouseup="onMouseUp">
    <div>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
      <span class="slider-strip"></span>
    </div>
    <div class="slider-thump" ref="slider_thump" @mousedown="onMouseDown"></div>
    <div class="slider-border-head"></div>
    <div class="slider-border-bottom"></div>
  </div>
</template>

<script>
const indexMin = 0
const indexMax = 145
// const indexDist = 0.2
// const stepDist = 3.846
export default {
  name: 'slider',
  data () {
    return {
      steps: 0,
      curSteps: 0,
      tempSteps: 0,
      mouseParams: {
        isMouseDown: false,
        startX: 0,
        startY: 0
      },
      sliderThump: null
    }
  },
  props: {
    parentSteps: {
      type: Number,
      default: 25
    }
  },
  mounted: function () {
    this.sliderThump = this.$refs.slider_thump
    this.curSteps = this.parentSteps
    this.steps = this.curSteps
    this.sliderThump.style.top = this.steps + 'px'
  },
  methods: {
    onMouseDown: function (ev) {
      this.mouseParams.isMouseDown = true
      this.mouseParams.startX = ev.clientX
      this.mouseParams.startY = ev.clientY
    },
    onMouseMove: function (ev) {
      if (!this.mouseParams.isMouseDown) return
      // console.log('move')
      this.steps = this.curSteps + (ev.clientY - this.mouseParams.startY)
      this.steps = (this.steps < indexMin ? indexMin : (this.steps > indexMax ? indexMax : this.steps))
      this.sliderThump.style.top = this.steps + 'px'
      this.$emit('onSliderStepChange', this.steps)
    },
    onMouseUp: function () {
      this.curSteps = this.steps
      this.mouseParams.isMouseDown = false
    },
    onMouseLeave: function () {
      this.curSteps = this.steps
      this.mouseParams.isMouseDown = false
    }
  },
  watch: {
    parentSteps (curV, oldV) {
      this.curSteps = curV
      this.steps = curV
    }
  }
}
</script>

<style scoped>
  * {
    user-select: none;
  }
  #slider-div {
    position: absolute;
    width: 52px;
    height: 160px;
    background-color: #0a191d;
    border: 2px solid #167685;
  }

  .slider-border-head, .slider-border-bottom {
    position: absolute;
    left: 4px;
    width: 44px;
    height: 2px;
    background-color: #0a191d;
  }

  .slider-border-head {
    top: -2px;
  }

  .slider-border-bottom {
    bottom: -2px;
  }

  .slider-strip {
    content: '';
    position: absolute;
    left: 15px;
    width: 22px;
    height: 1px;
    background-color: #103c48;
  }
  .slider-strip:nth-of-type(1)  {
    top: calc(3.846% * 1)
  }
  .slider-strip:nth-of-type(2)  {
    top: calc(3.846% * 2)
  }
  .slider-strip:nth-of-type(3)  {
    top: calc(3.846% * 3)
  }
  .slider-strip:nth-of-type(4)  {
    top: calc(3.846% * 4)
  }
  .slider-strip:nth-of-type(5)  {
    top: calc(3.846% * 5)
  }
  .slider-strip:nth-of-type(6)  {
    top: calc(3.846% * 6)
  }
  .slider-strip:nth-of-type(7)  {
    top: calc(3.846% * 7)
  }
  .slider-strip:nth-of-type(8)  {
    top: calc(3.846% * 8)
  }
  .slider-strip:nth-of-type(9)  {
    top: calc(3.846% * 9)
  }
  .slider-strip:nth-of-type(10)  {
    top: calc(3.846% * 10)
  }
  .slider-strip:nth-of-type(11)  {
    top: calc(3.846% * 11)
  }
  .slider-strip:nth-of-type(12)  {
    top: calc(3.846% * 12)
  }
  .slider-strip:nth-of-type(13)  {
    top: calc(3.846% * 13)
  }
  .slider-strip:nth-of-type(14)  {
    top: calc(3.846% * 14)
  }
  .slider-strip:nth-of-type(15)  {
    top: calc(3.846% * 15)
  }
  .slider-strip:nth-of-type(16)  {
    top: calc(3.846% * 16)
  }
  .slider-strip:nth-of-type(17)  {
    top: calc(3.846% * 17)
  }
  .slider-strip:nth-of-type(18)  {
    top: calc(3.846% * 18)
  }
  .slider-strip:nth-of-type(19)  {
    top: calc(3.846% * 19)
  }
  .slider-strip:nth-of-type(20)  {
    top: calc(3.846% * 20)
  }
  .slider-strip:nth-of-type(21)  {
    top: calc(3.846% * 21)
  }
  .slider-strip:nth-of-type(22)  {
    top: calc(3.846% * 22)
  }
  .slider-strip:nth-of-type(23)  {
    top: calc(3.846% * 23)
  }
  .slider-strip:nth-of-type(24)  {
    top: calc(3.846% * 24)
  }
  .slider-strip:nth-of-type(25)  {
    top: calc(3.846% * 25)
  }

  .slider-thump {
    cursor: pointer;
    position: absolute;
    left: 4px;
    top: 80px;
    width: 40px;
    height: 12px;
    border: 2px solid #188796;
    background-color: #12404b;
    opacity: 0.7;
    border-radius: 6px;
  }

  .slider-thump:before {
    position: absolute;
    content: '';
    top: 5px;
    left: 9px;
    width: 22px;
    height: 2px;
    background-color: #b9fcfd;
  }
</style>
