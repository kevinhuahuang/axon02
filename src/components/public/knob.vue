<template>
  <div class="knob-div" ref="knob_div" @mousedown="onMouseDown" @mousemove="onMouseMove" @mouseleave="onMouseLeave" @mouseup="onMouseUp">
    <div class="out-line">
      <div class="knob"></div>
    </div>
    <span ref="knob_spot" class="knob-spot"></span>
    <span class="progress-ground-bottom"></span>
    <span ref="progress_dynamic_left" class="progress-dynamic-left"></span>
    <span ref="progress_dynamic_top" class="progress-dynamic-top"></span>
    <span ref="progress_dynamic_right" class="progress-dynamic-right"></span>
    <span class="progress-ground-cover"></span>
  </div>
</template>
<script>
const centerX = 22
const centerY = 22
const radius = 10
const startAngular = 0
const endAngular = 270
const stepDist = (2 * Math.PI * radius) / 360
export default {
  name: 'knob',
  data () {
    return {
      mouseParams: {
        isMouseDown: false,
        startX: 0,
        startY: 0,
        curX: 0,
        curY: 0
      },
      knobSpot: null,
      progressLeft: null,
      progressTop: null,
      progressRight: null,
      steps: null,
      text: 'M',
      angle: '',
      curAngle: 0,
      cenX: 0,
      cenY: 0,
      isIncrease: null
    }
  },
  props: {
    parentText: {
      type: String,
      default: 'M'
    },
    parentSteps: {
      type: Number,
      default: 10
    },
    parentAngle: {
      type: Number,
      default: 10
    },
    parentType: {
      type: String,
      default: ''
    }
  },
  watch: {
    parentAngle (curV, oldV) {
      this.angle = curV
    }
  },
  mounted: function () {
    this.knobSpot = this.$refs.knob_spot
    this.progressLeft = this.$refs.progress_dynamic_left
    this.progressTop = this.$refs.progress_dynamic_top
    this.progressRight = this.$refs.progress_dynamic_right
    this.steps = this.parentSteps
    this.text = this.parentText
    this.curAngle = this.parentAngle
    this.rotateElement(this.curAngle)
  },
  methods: {
    onMouseDown: function (ev) {
      this.mouseParams.isMouseDown = true
      this.mouseParams.startX = ev.clientX
      this.mouseParams.startY = ev.clientY
      this.mouseParams.isMouseDown = true
      this.mouseParams.startX = ev.clientX
    },
    onMouseMove: function (ev) {
      if (!this.mouseParams.isMouseDown) return
      // this.getGestureAngular(this.getGestureType(ev.clientX, ev.clientY))
      // this.rotateElement(this.steps)
      // this.angle = this.curAngle + this.getTriangleAngle(this.mouseParams.startX, this.mouseParams.startY, ev.clientX, ev.clientY)
      // console.log('___this.angel:' + this.angle)
      // this.angle = this.getAngular(this.angle)
      // this.rotateElement(this.angle)
      let a, b, c
      a = ev.clientX - this.mouseParams.startX
      b = ev.clientY - this.mouseParams.startY
      c = Math.sqrt(a * a + b * b)
      // console.log('__a: ' + a + '   __b: ' + b)
      if ((a === 0) || (b === 0)) return
      if (this.isIncrease === null) {
        if (a > 0) {
          if (this.angle > 135) {
            if (b < 0) {
              this.isIncrease = false
              // console.log('__decrease')
            } else {
              this.isIncrease = true
              // console.log('___increase')
            }
          } else {
            this.isIncrease = true
            // console.log('___increase')
          }
        } else {
          if (this.angle < 135) {
            if (b < 0) {
              this.isIncrease = true
              // console.log('___increase')
            } else {
              this.isIncrease = false
              // console.log('__decrease')
            }
          } else {
            this.isIncrease = false
            // console.log('__decrease')
          }
        }
      }
      if (this.isIncrease) {
        this.angle = this.curAngle + c / stepDist
      } else {
        this.angle = this.curAngle - c / stepDist
      }
      this.angle = this.getAngular(this.angle)
      // console.log(this.angle)
      this.rotateElement(this.angle)
      this.$emit('onEffectDisplayChange', this.parentType, this.angle)
    },
    onMouseLeave: function () {
      this.mouseParams.isMouseDown = false
      this.curAngle = this.angle
      this.isIncrease = null
      // console.log('leave')
    },
    onMouseUp: function () {
      this.mouseParams.isMouseDown = false
      this.curAngle = this.angle
      this.isIncrease = null
      // console.log('up')
    },
    getAngular: function (angle) {
      if (isNaN(angle)) {
        angle = 0
      }
      return angle < startAngular ? startAngular : (angle > endAngular ? endAngular : angle)
    },
    rotateProgress: function (angular) {
      let deg = -135 + angular
      let degString = 'rotate(' + (-135 + angular) + 'deg)'
      if (deg < -45) {
        this.progressLeft.style.transform = degString
        this.progressTop.style.transform = degString
        this.progressRight.style.transform = degString
      } else if (deg < 45) {
        this.progressLeft.style.transform = 'rotate(-45deg)'
        this.progressTop.style.transform = degString
        this.progressRight.style.transform = degString
      } else {
        this.progressLeft.style.transform = 'rotate(-45deg)'
        this.progressTop.style.transform = 'rotate(45deg)'
        this.progressRight.style.transform = degString
      }
    },
    rotateSpot: function (angular) {
      // mouseParams.isLeftSide = angular > 135 ? false : true
      // console.log('angular:' + angular)
      let spotAngular = (2 * Math.PI / 360) * (45 - angular)
      let x = centerX + Math.sin(spotAngular) * radius
      let y = centerY - Math.cos(spotAngular) * radius
      this.knobSpot.style.top = x + 'px'
      this.knobSpot.style.left = y + 'px'
    },
    rotateElement: function (angular) {
      // console.log('___rotate angle:' + angular)
      this.rotateSpot(angular)
      this.rotateProgress(angular)
    },
    getGestureType: function (curX, curY) {
      let x = this.mouseParams.startX
      let y = this.mouseParams.startY
      let xType = (curX === x ? '' : (curX > x ? 'R' : 'L'))
      let yType = (curY === y ? '' : (curY > y ? 'D' : 'U'))
      return xType + yType
    },
    getGestureAngular: function (type) {
      switch (type) {
        case 'RU':
          // console.log('Right_Up')
          this.steps = this.steps + stepDist
          break
        case 'RD':
          // console.log('Right_Down')
          this.steps = this.steps + stepDist
          break
        case 'LU':
          // console.log('Left_Up')
          this.steps = this.steps - stepDist
          break
        case 'LD':
          // console.log('Left_Down')
          this.steps = this.steps - stepDist
          break
        default:
          break
      }
    },
    getTriangleAngle: function (startX, startY, endX, endY) {
      // this.cenX = this.$refs.knob_div.style.left + (this.$refs.knob_div.style.width + 1) / 2 // left = 0
      // this.cenY = this.$refs.knob_div.style.top + (this.$refs.knob_div.style.height + 1) / 2 // top = 0
      // console.log('___cenX: ' + this.cenX)
      // console.log('___cenY: ' + this.cenY)
      this.cenX = 1080
      this.cenY = 660
      let b1, b2, a, b, c, A, B
      b1 = Math.abs(endX - startX)
      b2 = Math.abs(endY - startY)
      a = Math.sqrt(b1 * b1 + b2 * b2)
      b1 = Math.abs(this.cenX - startX)
      b2 = Math.abs(this.cenY - startY)
      b = Math.sqrt(b1 * b1 + b2 * b2)
      b1 = Math.abs(this.cenX - endX)
      b2 = Math.abs(this.cenY - endY)
      c = Math.sqrt(b1 * b1 + b2 * b2)
      // console.log('___a: ' + a + '  ___b: ' + b + '  ___c: ' + c)
      A = (b * b + c * c - (a * a)) / (2 * b * c)
      // console.log('___cosa: ' + A)
      B = (A * 360) / (2 * Math.PI)
      // console.log('___move angle: ' + B)
      return B
    }
  }
}
</script>
<style scoped>
  * {
    user-select: none;
  }
  .knob-div {
    cursor: pointer;
    position: absolute;
    width: 50px;
    height: 50px;
    /*clip: rect(32px, 64px, 64px, 0px);*/
  }
  .progress-ground-bottom {
    position: absolute;
    top: 0;
    left: 0;
    width: 44px;
    height: 44px;
    border: 4px solid #273d40;
    border-radius: 28px;
  }
  .out-line {
    position:absolute;
    top: 8px;
    left: 8px;
    width: 36px;
    height: 36px;
    background: #9ccdcd;
    border-radius: 18px;
  }
  .knob {
    position:absolute;
    top: 2px;
    left: 2px;
    width: 32px;
    height: 32px;
    background: #0a1215;
    border-radius: 17px;
  }
  .knob-spot {
    position: absolute;
    width:8px;
    height: 8px;
    background: #9ccdcd;
    border-radius: 4px;
  }
  .progress-ground-cover {
    position: absolute;
    width: 44px;
    height: 44px;
    border: 4px solid #0a191d;
    border-radius: 28px;
    clip: rect(0px, 28px, 28px, 0px);
    -webkit-transform: rotate(-135deg); /* 90 + 45*/
  }
  .progress-dynamic-left {
    position: absolute;
    width: 44px;
    height: 44px;
    border: 4px solid #135f6c;
    border-radius: 28px;
    clip: rect(0px, 28px, 28px, 0px);
    -webkit-transform: rotate(-100deg); /* start from -135 to -45*/
  }
  .progress-dynamic-top {
    position: absolute;
    width: 44px;
    height: 44px;
    border: 4px solid #135f6c;
    border-radius: 28px;
    clip: rect(0px, 28px, 28px, 0px);
    -webkit-transform: rotate(-135deg); /* start from -45 to 45 */
  }
  .progress-dynamic-right {
    position: absolute;
    width: 44px;
    height: 44px;
    border: 4px solid #135f6c;
    border-radius: 28px;
    clip: rect(0px, 28px, 28px, 0px);
    -webkit-transform: rotate(-135deg); /* start from 45 to 135*/
  }
</style>
