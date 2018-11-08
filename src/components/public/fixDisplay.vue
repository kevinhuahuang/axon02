<template>
  <div class="fix_display">
    <span class="data_type" v-text="dataType"></span>
    <span class="data_value" v-text="dataValue"></span>
  </div>
</template>

<script>
export default {
  name: 'fixDisplay',
  data () {
    return {
      dataType: '',
      dataValue: ''
    }
  },
  mounted: function () {
    this.dataType = this.parentType
    this.dataValue = this.parentValue
  },
  methods: {
  },
  props: {
    parentType: {
      type: String,
      default: 'FLT WIDTH'
    },
    parentValue: {
      type: String,
      default: '11'
    }
  },
  watch: {
    parentValue (curV, oldV) {
      this.dataValue = curV
    }
  }
}
</script>

<style scoped>
  .fix_display {
    position: absolute;
    width: 65px;
    height: 50px;
  }
  .data_type {
    position: absolute;
    top: 10px;
    font-family: Arial, serif;
    font-size: 10px;
    font-weight: 100;  /* <500 not work*/
    color: #a1d1d0;
  }
  .data_value {
    position: absolute;
    top: 30px;
    left: 15px;
    font-family: Arial, serif;
    font-size: 10px;
    font-weight: 100;  /* <500 not work*/
    color: #a1d1d0;
  }
</style>
