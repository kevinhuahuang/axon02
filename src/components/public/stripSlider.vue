<template>
  <div class="strip-slider-div" @mousemove="onMouseMove" @mouseup="onMouseUp" @mouseleave="onMouseLeave">
    <span class="strip-slider-border-head"></span>
    <span class="strip-slider-border-foot"></span>
    <span class="strip-slider-progress" ref="slider_progress"></span>
    <span class="strip-slider-square" ref="slider_square" @mousedown="onMouseDown"></span>
  </div>
</template>

<script>
const minX = 5
const maxX = 40
export default {
  name: 'stripSlider',
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
      default: 10
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
      this.sliderProgress.style.width = (stepX - 5) + 'px'
    }
  }
}
</script>

<style scoped>
  * {
    user-select: none;
  }

  .strip-slider-div {
    position: absolute;
    width: 50px;
    height: 18px;
    background-color: #0c2e35;
    border: 2px solid #1a96a4;
    border-radius: 1px;
  }

  .strip-slider-border-head, .strip-slider-border-foot {
    position: absolute;
    left: 2px;
    width: 46px;
    height: 2px;
    background-color: #0a191d;
  }

  .strip-slider-border-head {
    top: -2px;
  }

  .strip-slider-border-foot {
    bottom: -2px;
  }

  .strip-slider-progress {
    position: absolute;
    left: 5px;
    width: 0;
    height: 18px;
    background-color: #137684;
  }

  .strip-slider-square {
    cursor: pointer;
    position: absolute;
    left: 5px;
    width: 5px;
    height: 18px;
    border-radius: 1px;
    background-color: #a5d8d8;
  }
</style>
