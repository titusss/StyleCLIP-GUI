<template>
  <!-- <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
  <div>
      <FaderSlider v-for="n in faderSliderAmount" :key="n"/>
  </div>
</template>

<script>
// @ is an alias to /src
import FaderSlider from '@/components/FaderSlider.vue'

export default {
  name: 'HomeView',
  components: {
    FaderSlider
  },
  data () {
    return {
      faderSliderAmount: 5
    }
  }
}
</script>
