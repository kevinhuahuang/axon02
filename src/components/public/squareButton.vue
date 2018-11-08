<template>
  <div class="square-button-div" :class="[isPress ? buttonPress : buttonRelease]" @click="onClick" :style="{width:buttonWidth, height:buttonHeight}">
    <label class="square-button-word" v-text="text" :style="{fontSize: textSize}"></label>
  </div>
</template>

<script>
export default {
  name: 'squareButton',
  data () {
    return {
      isPress: false,
      buttonPress: 'square-button-div-true',
      buttonRelease: 'square-button-div-false'
    }
  },
  methods: {
    onClick: function () {
      this.isPress = !this.isPress
      // console.log('click')
    }
  },
  props: {
    text: {
      type: String,
      default: 'M'
    },
    buttonWidth: {
      type: String,
      default: '18px'
    },
    buttonHeight: {
      type: String,
      default: '18px'
    },
    textTop: {
      type: String,
      default: '4px'
    },
    textLeft: {
      type: String,
      default: '6px'
    },
    textSize: {
      type: String,
      default: '50%'
    }
  }
}
</script>

<style scoped>
  * {
    user-select: none;
  }
  .square-button-div-true {
    position: absolute;
    width: 18px;
    height: 18px;
    background-color: #125d6a;
    border-radius: 1px;
  }

  .square-button-div-false {
    position: absolute;
    width: 18px;
    height: 18px;
    background-color: #0c2e35;
    border-radius: 1px;
  }

  .square-button-word{
    position: absolute;
    top: 3px;
    left: 4px;
    font-family: Arial, serif;
    font-weight: 100;  /* <500 not work*/
    font-stretch: ultra-condensed; /* not work*/
    color: #a1d1d0;
  }
</style>
