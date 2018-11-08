<template>
  <div id="network">
    <span class="border-top"></span>
    <span class="border-right"></span>
    <span class="border-left"></span>
    <span class="border-bottom"></span>
    <square-button class="network-button" :textSize="textSize" :text="buttonText" :buttonWidth="buttonW" :buttonHeight="buttonH" :textTop="textT" :textLeft="textL"></square-button>
    <div class="circle-button-segment">
      <circle-button class="circle-button circle-button1"></circle-button>
      <circle-button class="circle-button circle-button2"></circle-button>
      <circle-button class="circle-button circle-button3"></circle-button>
      <circle-button class="circle-button circle-button4"></circle-button>
      <circle-button class="circle-button circle-button5"></circle-button>
      <circle-button class="circle-button circle-button6"></circle-button>
      <circle-button class="circle-button circle-button7"></circle-button>
      <svg xmlns="http://www.w3.org/2000/svg" version="1.1" ref="net_svg" style="width:100%; height:100%;" ></svg>
    </div>
    <div class="network-button-segment">
      <network-square-button parentText="00" class="network-square-button network-square-button1"></network-square-button>
      <network-square-button parentText="01" class="network-square-button network-square-button2"></network-square-button>
      <network-square-button parentText="02" class="network-square-button network-square-button3"></network-square-button>
      <network-square-button parentText="03" class="network-square-button network-square-button4"></network-square-button>
      <network-square-button parentText="04" class="network-square-button network-square-button5"></network-square-button>
      <network-square-button parentText="05" class="network-square-button network-square-button6"></network-square-button>
      <network-square-button parentText="06" class="network-square-button network-square-button7"></network-square-button>
      <svg xmlns="http://www.w3.org/2000/svg" version="1.1" ref="button_svg" style="width:100%; height:100%" ></svg>
    </div>
  </div>
</template>

<script>
import CircleButton from './public/circleButton'
import SquareButton from './public/squareButton'
import NetworkSquareButton from './public/networkSquareButton'
export default {
  name: 'networkSegment',
  components: {NetworkSquareButton, SquareButton, CircleButton},
  data () {
    return {
      buttonText: 'NETWORK',
      buttonW: '73px',
      buttonH: '20px',
      textT: '4px',
      textL: '6px',
      textSize: '50%',
      netSvg: null,
      buttonSvg: null
    }
  },
  mounted: function () {
    this.initNetworkLine()
  },
  methods: {
    initNetworkLine: function () {
      this.netSvg = this.$refs.net_svg
      let line = document.createElementNS('http://www.w3.org/2000/svg', 'polyline')
      let points = '25, 75, 110, 25, 200, 75, 110, 230, 200, 175, 110, 125, 25, 175, 110, 230, 25, 75, 110, 25, 110, 125, 25, 175, 110, 25, 200, 175, 110, 125, 225, 125'
      line.setAttribute('points', points)
      line.setAttribute('stroke', '#66a2a6')
      line.setAttribute('stroke-width', '2px')
      this.netSvg.appendChild(line)

      this.buttonSvg = this.$refs.button_svg
      line = document.createElementNS('http://www.w3.org/2000/svg', 'line')
      line.setAttribute('x1', '0')
      line.setAttribute('y1', '125')
      line.setAttribute('x2', '100')
      line.setAttribute('y2', '125')
      line.setAttribute('stroke', '#66a2a6')
      line.setAttribute('stroke-width', '2px')
      this.buttonSvg.appendChild(line)

      line = document.createElementNS('http://www.w3.org/2000/svg', 'line')
      line.setAttribute('x1', '60')
      line.setAttribute('y1', '15')
      line.setAttribute('x2', '60')
      line.setAttribute('y2', '237')
      line.setAttribute('stroke', '#66a2a6')
      line.setAttribute('stroke-width', '2px')
      this.buttonSvg.appendChild(line)

      line = document.createElementNS('http://www.w3.org/2000/svg', 'line')
      line.setAttribute('x1', '60')
      line.setAttribute('y1', '15')
      line.setAttribute('x2', '100')
      line.setAttribute('y2', '15')
      line.setAttribute('stroke', '#66a2a6')
      line.setAttribute('stroke-width', '2px')
      this.buttonSvg.appendChild(line)

      line = document.createElementNS('http://www.w3.org/2000/svg', 'line')
      line.setAttribute('x1', '60')
      line.setAttribute('y1', '52')
      line.setAttribute('x2', '100')
      line.setAttribute('y2', '52')
      line.setAttribute('stroke', '#66a2a6')
      line.setAttribute('stroke-width', '2px')
      this.buttonSvg.appendChild(line)

      line = document.createElementNS('http://www.w3.org/2000/svg', 'line')
      line.setAttribute('x1', '60')
      line.setAttribute('y1', '89')
      line.setAttribute('x2', '100')
      line.setAttribute('y2', '89')
      line.setAttribute('stroke', '#66a2a6')
      line.setAttribute('stroke-width', '2px')
      this.buttonSvg.appendChild(line)

      line = document.createElementNS('http://www.w3.org/2000/svg', 'line')
      line.setAttribute('x1', '60')
      line.setAttribute('y1', '163')
      line.setAttribute('x2', '100')
      line.setAttribute('y2', '163')
      line.setAttribute('stroke', '#66a2a6')
      line.setAttribute('stroke-width', '2px')
      this.buttonSvg.appendChild(line)

      line = document.createElementNS('http://www.w3.org/2000/svg', 'line')
      line.setAttribute('x1', '60')
      line.setAttribute('y1', '200')
      line.setAttribute('x2', '100')
      line.setAttribute('y2', '200')
      line.setAttribute('stroke', '#66a2a6')
      line.setAttribute('stroke-width', '2px')
      this.buttonSvg.appendChild(line)

      line = document.createElementNS('http://www.w3.org/2000/svg', 'line')
      line.setAttribute('x1', '60')
      line.setAttribute('y1', '237')
      line.setAttribute('x2', '100')
      line.setAttribute('y2', '237')
      line.setAttribute('stroke', '#66a2a6')
      line.setAttribute('stroke-width', '2px')
      this.buttonSvg.appendChild(line)
    }
  }
}
</script>

<style scoped>
  #network {
    position: absolute;
    width: 436px;
    height: 270px;
    background-color: #05090b;
    border: 2px solid #66a2a6;
  }
  .border-top, .border-bottom {
    position: absolute;
    left: 10px;
    width: 416px;
    height:2px;
    background-color: #05090b;
  }
  .border-top {
    top: -2px;
  }
  .border-bottom {
    bottom: -2px;
  }
  .border-left, .border-right {
    position: absolute;
    top: 10px;
    width: 2px;
    height: 250px;
    background-color: #05090b;
  }
  .border-left {
    left: -2px;
  }
  .border-right {
    right: -2px;
  }
  .network-button {
    position: absolute;
    top: 10px;
    left: 10px;
  }
  .circle-button-segment {
    position: absolute;
    top: 10px;
    left: 50px;
    width: 225px;
    height: 255px;
  }
  .circle-button {
    position: absolute;
  }
  .circle-button1 {
    top: 50px;
    left: 0;
  }
  .circle-button2 {
    top: 0;
    left: 85px;
  }
  .circle-button3 {
    top: 50px;
    right: 0;
  }
  .circle-button4 {
    top: 150px;
    right: 0
  }
  .circle-button5 {
    bottom: 0;
    left: 85px;
  }
  .circle-button6 {
    top: 150px;
    left: 0;
  }
  .circle-button7 {
    top: 100px;
    left: 85px
  }
  .network-button-segment {
    position: absolute;
    top: 10px;
    left: 275px;
    width: 160px;
    height: 255px;
  }

  .network-square-button {
    position: absolute;
    left: 100px;
  }
  .network-square-button1 {
    top: 2px;
  }
  .network-square-button2 {
    top: 39px;
  }
  .network-square-button3 {
    top: 76px;
  }
  .network-square-button4 {
    top: 113px;
  }
  .network-square-button5 {
    top: 150px;
  }
  .network-square-button6 {
    top: 187px;
  }
  .network-square-button7 {
    top: 224px;
  }
</style>
