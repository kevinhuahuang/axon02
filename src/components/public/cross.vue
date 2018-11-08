<template>
  <div id="cross-big-div" class="cross-big-div" @mousemove="onMouseMove" @mouseup="onMouseUp" @mouseleave="onMouseLeave">
    <span class="cross-big-border-head"></span>
    <span class="cross-big-border-foot"></span>
    <span class="cross-big-vertical-line" ref="vertical_line"></span>
    <span class="cross-big-horizontal-line" ref="horizontal_line"></span>
    <span class="cross-big-square" @mousedown="onMouseDown" ref="square_el"></span>
    <span class="cross-big-notice" v-text="crossNotice"></span>
  </div>
</template>

<script>
const minX = 0
const maxX = 172
const minY = 0
const maxY = 172
export default {
  name: 'cross',
  data () {
    return {
      stepX: 0,
      stepY: 0,
      curStepX: 0,
      curStepY: 0,
      mouseParams: {
        isMouseDown: false,
        startX: 0,
        startY: 0
      },
      verticalLine: null,
      horizontalLine: null,
      squareEl: null,
      crossNotice: '[10,20]'
    }
  },
  props: {
    parentStepX: {
      type: Number,
      default: 10
    },
    parentStepY: {
      type: Number,
      default: 20
    }
  },
  watch: {
    parentStepX (curV, oldV) {
      this.curStepX = curV
    },
    parentStepY (curV, oldV) {
      this.curStepY = curV
    }
  },
  mounted: function () {
    this.verticalLine = this.$refs.vertical_line
    this.horizontalLine = this.$refs.horizontal_line
    this.squareEl = this.$refs.square_el
    this.curStepX = this.parentStepX
    this.curStepY = this.parentStepY
    this.moveSquare(this.curStepX, this.curStepY)
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
      this.stepY = this.curStepY + ev.clientY - this.mouseParams.startY

      this.stepX = (this.stepX < minX ? minX : (this.stepX > maxX ? maxX : this.stepX))
      this.stepY = (this.stepY < minY ? minY : (this.stepY > maxY ? maxY : this.stepY))
      this.moveSquare(this.stepX, this.stepY)
      this.crossNotice = '[' + Math.floor(this.stepX) + ',' + Math.floor(this.stepY) + ']'
    },
    onMouseUp: function () {
      this.mouseParams.isMouseDown = false
      this.curStepX = this.stepX
      this.curStepY = this.stepY
    },
    onMouseLeave: function () {
      this.mouseParams.isMouseDown = false
      this.curStepX = this.stepX
      this.curStepY = this.stepY
    },
    moveSquare: function (stepX, stepY) {
      this.squareEl.style.top = stepY + 'px'
      this.squareEl.style.left = stepX + 'px'
      this.verticalLine.style.left = stepX + 6 + 'px'
      this.horizontalLine.style.top = stepY + 6 + 'px'
    }
  }
}
</script>

<style scoped>
  * {
    user-select: none;
  }
  #cross-big-div {
    position: absolute;
    width: 184px;
    height: 184px;
    border: 2px solid #188796;
  }

  .cross-big-border-head, .cross-big-border-foot {
    position: absolute;
    left: 5px;
    width: 174px;
    height: 2px;
    background-color: #0a1215;
  }

  .cross-big-border-head {
    top: -2px;
  }

  .cross-big-border-foot {
    bottom: -2px;
  }

  .cross-big-square {
    cursor: pointer;
    position: absolute;
    top: 87px;
    left: 87px;
    width: 10px;
    height: 10px;
    background-color: #125c6a;
    border: 1px solid #a5d8d8;
  }

  .cross-big-vertical-line {
    position: absolute;
    top: 0;
    left: 50%;
    width: 2px;
    height: 184px;
    background-color: #0e373e;
  }

  .cross-big-horizontal-line {
    position: absolute;
    top: 50%;
    left: 0;
    width: 184px;
    height: 2px;
    background-color: #0e373e;
  }
  .cross-big-notice {
    position: absolute;
    top: 5px;
    right: 10px;
    font-size: 12px;
    font-weight: bold;
    color:  #a5d8d8;
  }
</style>
