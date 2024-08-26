<template>
  <div>
    <ul class="progress-bars">
      <li
        v-for="(step, index) in steps"
        :key="index"
        :class="{ active: value === index + 1, completed: value > index + 1 }"
        @click="updateStep(index + 1)"
      >
        <span class="sub-header font-weight-bold" style="margin-top: 30px; color: #2097F3; display: block;">
          {{ step.title }}
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'stepper-vue',
  props: {
    value: {
      type: Number,
      default: 1,
    },
    steps: {
      type: Array,
      default: () => [
        { step: 1, title: "First Title" },
        { step: 2, title: "Manage Tasks" }
      ]
    }
  },
};
</script>


<style lang="scss" scoped>
.steps-content {
  margin-top: 30px;
  color: #fff;
}
.steps-content p {
  font-size: 12px;
  margin-top: 15px;
}
.progress-bars {
  list-style: none;
  margin-top: 30px;
  z-index: 0;
  padding: 0;
  display: flex; /* Make the steps horizontal */
  font-size: 13px;
  font-weight: 700;
  counter-reset: containerReg 0;
}
.progress-bars li {
  position: relative;
  text-align: center;
  flex: 1; /* Distribute space equally */
  margin-left: 40px;
  counter-increment: containerReg 1;
  color: #4f6581;
}
.progress-bars li::before {
  content: "";
  line-height: 25px;
  text-align: center;
  position: absolute;
  height: 25px;
  width: 25px;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  left: 49%;
  transform: translateX(-50%); /* Center the step indicator */
  top: -5px;
  z-index: 0;
  background-image: url(./empty_step.svg);
}
.progress-bars li.active::before {
  background-image: url(./active.png);
}
.progress-bars li.completed::before {
  background-image: url(./completed_step.svg);
}
.progress-bars li::after {
  content: "";
  position: absolute;
  height: 2px; /* Connector line thickness */
  width: 100%; /* Stretch connector line */
  background-color: #2097f3;
  z-index: 1;
  top: 7px; /* Position line to center with indicators */
  left: -3%;
  transform: translateX(-50%);
}
.progress-bars li.completed::after,
.progress-bars li.active::after {
  background-color: #2097f3;
}
.progress-bars li:first-child:after {
  display: none;
}
</style>
