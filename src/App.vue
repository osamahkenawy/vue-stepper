<template>
  <div id="app">
    <stepper-vue v-model="step" :steps="steps" />
    <!-- Conditional rendering of placeholder images based on the step value -->
    <div>
      <img v-if="step === 1" src="https://via.placeholder.com/500x600?text=Form+1" alt="Form 1 Image" />
      <img v-if="step === 2" src="https://via.placeholder.com/500x600?text=Form+2" alt="Form 2 Image" />
    </div>
     
  </div>
</template>

<script>
import StepperVue from './components/Stepper/StepperVue.vue';

export default {
  name: 'App',
  data() {
    return {
      step: 1,
      steps: [
        { step: 1, title: "First Form" },
        { step: 2, title: "Second Form" }
      ],
    }
  },
  components: {
    StepperVue
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
