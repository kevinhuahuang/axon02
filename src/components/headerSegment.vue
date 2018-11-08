<template>
  <div id="header">
    <div class="header-left-div"><label class="header-left">AXON 02</label></div>
    <div class="header-right-div"><label class="header-right">AUDIODAMAGE</label></div>
  </div>
</template>

<script>
export default {
  name: 'headerSegment',
  components: {}
}
</script>

<style scoped>
  #header {
    position: absolute;
    width: 1050px;
    height: 46px;
    background-color: #092f35;
  }
  .header-left-div {
    position: absolute;
    width: 147px;
    height: 46px;
    background-color: #092f35;
  }
  .header-left {
    position: absolute;
    top: 8px;
    left: 10px;
    width: 100%;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    font-size: 28px;
    font-weight: bold;
    color: #4e6767;
  }

  .header-right-div {
    position: absolute;
    right: 18px;
    width: 110px;
    height: 46px;
    background-color: #092f35;
  }
  .header-right {
    position: absolute;
    top: 15px;
    width: 100%;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    font-size: 16px;
    font-weight: bold;
    color: #4e6767;
  }
</style>
