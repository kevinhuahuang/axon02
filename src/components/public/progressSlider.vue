<template>
  <div class="progress-slider-div" @mousemove="onMouseMove" @mouseup="onMouseUp" @mouseleave="onMouseLeave">
    <span class="progress-slider-progress" ref="slider_progress"></span>
    <span class="progress-slider-square"  ref="slider_square" @mousedown="onMouseDown"></span>
  </div>
</template>

<script>
const minX = 0
const maxX = 60
export default {
  name: 'progressSlider',
  data () {
    return {
      stepX: 0,
      curStepX: 0,
      mouseParams: {
        isMouseDown: false,
        startX: 0,
        startY: 0
      },
      sliderProgress: null,
      sliderSquare: null
    }
  },
  props: {
    parentStepX: {
      type: Number,
      default: 15
    }
  },
  mounted: function () {
    this.sliderProgress = this.$refs.slider_progress
    this.sliderSquare = this.$refs.slider_square
    this.moveProgress(this.curStepX)
  },
  methods: {
    onMouseDown: function (ev) {
      this.mouseParams.isMouseDown = true
      this.mouseParams.startX = ev.clientX
      this.mouseParams.startY = ev.clientY
    },
    onMouseMove: function (ev) {
      if (!this.mouseParams.isMouseDown) return
      this.stepX = this.curStepX + ev.clientX - this.mouseParams.startX
      this.stepX = (this.stepX < minX ? minX : (this.stepX > maxX ? maxX : this.stepX))
      this.moveProgress(this.stepX)
    },
    onMouseUp: function () {
      this.mouseParams.isMouseDown = false
      this.curStepX = this.stepX
    },
    onMouseLeave: function () {
      this.mouseParams.isMouseDown = false
      this.curStepX = this.stepX
    },
    moveProgress: function (stepX) {
      this.sliderSquare.style.left = stepX + 'px'
      this.sliderProgress.style.width = this.stepX + 'px'
    }
  }
}
</script>

<style scoped>
  * {
    user-select: none;
  }
  .progress-slider-div {
    position: absolute;
    width: 60px;
    height: 12px;
    background-color: #0c2e35;
    border-radius: 1px;
  }
  .progress-slider-progress {
    position: absolute;
    width: 0;
    height: 12px;
    background-color: #137684;
  }
  .progress-slider-square {
    cursor: pointer;
    position: absolute;
    left: 10px;
    width: 6px;
    height: 12px;
    border-radius: 1px;
    background-color: #a5d8d8;
  }
</style>
