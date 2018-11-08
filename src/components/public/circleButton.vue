<template>
  <div class="circle-button-div" @click="onClick">
    <div class="outside" :class="[isPress ? outsidePress : outsideRelease]"></div>
    <div class="middle" :class="[isPress ? middlePress : middleRelease]"></div>
    <div class="inside" :class="[isPress ? insidePress : insideRelease]"></div>
    <div class="dot" :class="[isPress ? dotPress : dotRelease]"></div>
  </div>
</template>

<script>
export default {
  name: 'circleButton',
  data () {
    return {
      outsidePress: 'outside-press',
      outsideRelease: 'outside-release',
      middlePress: 'middle-press',
      middleRelease: 'middle-release',
      insidePress: 'inside-press',
      insideRelease: 'inside-release',
      dotPress: 'dot-press',
      dotRelease: 'dot-release',
      isPress: false
    }
  },
  mounted: function () {
    this.isPress = this.parentPress
  },
  methods: {
    onClick: function () {
      this.isPress = !this.isPress
    }
  },
  props: {
    parentPress: {
      type: Boolean,
      default: false
    }
  },
  watch: {
    parentPress (curV, oldV) {
      this.isPress = curV
    }
  }
}
</script>

<style scoped>
  * {
    user-select: none;
  }
  .circle-button-div {
    position: absolute;
    width: 50px;
    height: 50px;
    background-color: #05090b;
  }
  .outside {
    position: absolute;
    width: 46px;
    height: 46px;
    border: 2px solid #125d6b;
    border-radius: 25px;
   opacity: 1;
  }
  .outside-press {
    background-color: #0b161a;
   opacity: 1;
  }
  .outside-release {
    background-color: #0e2e35;
   opacity: 1;
  }
  .middle {
    position: absolute;
    top: 4px;
    left: 4px;
    width: 38px;
    height: 38px;
    background-color: #0b161a;
    border: 2px solid red;
    border-radius: 21px;
   opacity: 1;
  }
  .middle-press {
    border: 2px solid red;
   opacity: 1;
  }
  .middle-release {
    background-color: #0e2e35;
    border: 2px solid #0e2e35;
   opacity: 1;
  }
  .inside {
    position: absolute;
    top: 9px;
    left: 9px;
    width: 28px;
    height: 28px;
    background-color: #0b161a;
    border: 2px solid #a0d2d2;
    border-radius: 16px;
   opacity: 1;
  }
  .inside-press {
    background-color: #0b161a;
    border: 2px solid #0b161a;
   opacity: 1;
  }
  .inside-release {
    background-color: #0e2e35;
    border: 2px solid #0e2e35;
   opacity: 1;
  }
  .dot {
    position: absolute;
    top: 15px;
    left: 15px;
    width: 20px;
    height: 20px;
    background-color: #66a2a6;
    border-radius: 10px;
  }
  .dot-press {
    background-color: #66a2a6;
  }
  .dot-release {
    background-color: #125d6a;
  }
</style>
