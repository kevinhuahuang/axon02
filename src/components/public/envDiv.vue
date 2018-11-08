<template>
  <div class="env_div">
    <div class="amp_env">
      <progress-slider class="attack_amp"></progress-slider>
      <progress-slider class="curve_amp"></progress-slider>
      <progress-slider class="release_amp"></progress-slider>
      <progress-slider class="re_curve_amp"></progress-slider>
      <span class="amp_text amp_attack">ATTACK</span>
      <span class="amp_text amp_attack_curve">A_CURVE</span>
      <span class="amp_text amp_release">RELEASE</span>
      <span class="amp_text amp_release_curve">R_CURVE</span>
    </div>
    <div class="pitch_env">
      <progress-slider class="attack_pitch"></progress-slider>
      <progress-slider class="curve_pitch"></progress-slider>
      <progress-slider class="release_pitch"></progress-slider>
      <progress-slider class="re_curve_pitch"></progress-slider>
      <progress-slider class="amount_pitch"></progress-slider>
      <span class="pitch_text pitch_attack">ATTACK</span>
      <span class="pitch_text pitch_attack_curve">A_CURVE</span>
      <span class="pitch_text pitch_release">RELEASE</span>
      <span class="pitch_text pitch_release_curve">R_CURVE</span>
      <span class="pitch_text pitch_amount">AMOUNT</span>
    </div>
  </div>
</template>

<script>
import ProgressSlider from './progressSlider'
export default {
  name: 'envDiv',
  components: {ProgressSlider},
  data () {
    return {}
  },
  mounted: function () {
  },
  methods: {
  },
  props: {
  }
}
</script>

<style scoped>
  .env_div {
    position: absolute;
    width: 300px;
    height: 125px;
    background-color: #0a191d;
  }
  .amp_env {
    position: absolute;
    left:2px;
    top: 2px;
  }
  .attack_amp, .attack_pitch, .amp_attack, .pitch_attack {
    top:5px;
  }
  .curve_amp, .curve_pitch, .amp_attack_curve, .pitch_attack_curve{
    top: 30px;
  }
  .release_amp, .release_pitch, .amp_release, .pitch_release {
    top: 55px;
  }
  .re_curve_amp, .re_curve_pitch, .amp_release_curve, .pitch_release_curve{
    top: 80px;
  }
  .pitch_env {
    position: absolute;
    top: 2px;
    left: 150px;
  }
  .amount_pitch, .pitch_amount {
    top: 105px;
  }
  .amp_text, .pitch_text {
    position: absolute;
    left: 70px;
    font-family: Arial, serif;
    font-size: 10px;
    font-weight: 100;  /* <500 not work*/
    color: #a1d1d0;
  }
</style>
