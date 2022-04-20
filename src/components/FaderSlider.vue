<template>
  <div class="wrapper">
    <div class="faderField">
      <input
        type="range"
        :min="sliderMin"
        :max="sliderMax"
        step="2"
        v-model="sliderValue"
        class="faderSlider verticalSlider allCenter"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'FaderSlider',
  computed: {
    sliderBackground () {
      return this.sliderValue < this.sliderMax / 2
        ? 'linear-gradient(to top, #000 0%, #000 100%)' + ',' +
          'linear-gradient(to right, #c6c6c6 0%, #c6c6c6 ' + this.sliderValue + '%, #4A4A4A ' + this.sliderValue + '% , #4A4A4A 100%)'
        : 'linear-gradient(to top, #000 0%, #000 100%)' + ',' +
          'linear-gradient(to right, #4A4A4A 0%, #4A4A4A ' + this.sliderValue + '%, #c6c6c6 ' + this.sliderValue + '% , #c6c6c6 100%)'
    }
  },
  data () {
    return {
      sliderValue: 50,
      sliderMin: 0,
      sliderMax: 100
    }
  }
}
</script>

<style scoped>
.wrapper {
  --component-width: 10vw;
  --component-height: 60vh;
  width: var(--component-width);
  height: var(--component-height);
  display: inline-block;
  padding: 10px;
}
.faderField {
  background-color: #eaeaea;
  transform: rotate(270deg);
  transform-origin: calc(var(--component-height) / 2) calc(var(--component-height) / 2);
  height: var(--component-width);
  width: var(--component-height);
  border-radius: 25px;
}
.allCenter {
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

input {
  padding: 8px;
  -webkit-appearance: none; /* Override default CSS styles */
  appearance: none;
  width: 80%; /* Full-width */
  height: 3px; /* Specified height */
  background: #000; /* Grey background */
  border-radius: 100px;
  box-shadow: inset -2px 1px 2px rgba(0, 0, 0, 0.65), -1px 1px 0px #fff;
  /* background-image: linear-gradient(to bottom, #000 0%, #000 100%),
    linear-gradient(to bottom, #c6c6c6 0%, #c6c6c6 100%); */
  background-image: v-bind(sliderBackground);
  background-clip: content-box, padding-box;
  outline: none;
}
input::-webkit-slider-thumb {
  -webkit-appearance: none; /* Override default look */
  appearance: none;
  width: 85px; /* Set a specific slider handle width */
  height: 50px; /* Slider handle height */
  background: linear-gradient(
    to left,
    rgba(193, 193, 193, 1) 0%,
    rgba(255, 255, 255, 1) 78%,
    rgba(162, 162, 162, 1) 79%,
    rgba(224, 224, 224, 1) 99%,
    rgba(193, 193, 193, 1) 100%
  );
  cursor: pointer; /* Cursor on hover */
  -moz-box-shadow: inset -1px 1px 0 #fff, -30px 0px 35px -15px rgba(0, 0, 0, 1);
  -webkit-box-shadow: inset -1px 1px 0 #fff,
    -30px 0px 35px 15px rgba(0, 0, 0, 1);
  box-shadow: inset -1px 1px 0 #fff, -30px 0px 35px -15px rgba(0, 0, 0, 1);
}
</style>
