<template>
  <div class="square-button-div" :class="[isPress ? buttonPress : buttonRelease]" @click="onClick">
    <label class="square-button-word" v-text="text"></label>
  </div>
</template>

<script>
export default {
  name: 'networkSquareButton',
  data () {
    return {
      isPress: false,
      buttonPress: 'square-button-div-true',
      buttonRelease: 'square-button-div-false',
      text: ''
    }
  },
  mounted: function () {
    this.text = this.parentText
  },
  methods: {
    onClick: function () {
      this.isPress = !this.isPress
      // console.log('click')
    }
  },
  props: {
    parentText: {
      type: String,
      default: '01'
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
    width: 38px;
    height: 22px;
    background-color: #125d6a;
    border: 2px solid #125d6a;
    border-radius: 1px;
  }

  .square-button-div-false {
    position: absolute;
    width: 38px;
    height: 22px;
    background-color: #0c2e35;
    border: 2px solid #125d6a;
    border-radius: 1px;
  }

  .square-button-word{
    position: absolute;
    top: 4px;
    right: 4px;
    font-family: Arial, serif;
    font-size: 60%;
    font-weight: 100;  /* <500 not work*/
    font-stretch: ultra-condensed; /* not work*/
    color: #a1d1d0;
  }
</style>
