<template>
  <div class="centered-container">
    <div>
      {{ timer }}
      <div v-if="!start" class="buttonContainer">
        <div @click="start = !start; $emit('start')" id="start">Start</div>
      </div>
      <div v-else class="buttonContainer">
        <div @click="start = !start; $emit('stop')" id="stop">Stop</div>
      </div>
      <div @click="_reset" id="reset" class="buttonContainer">Reset</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      start: null,
    };
  },
  methods: {
    _reset() {
      if (this.start === true) {
        this.start = false;
      }
      this.$emit('reset');
    },
  },
  name: 'Timer',
  props: ['timer', 'state'],
};
</script>

<style>
.centered-container {
  display: flex;
  justify-content: center; /* Center horizontally */
  align-items: center; /* Center vertically */
}
.buttonContainer {
  padding-left: 10%;
}
#start,
#stop,
#reset {
  cursor: pointer;
  width: 100px; /* Adjust the width as needed */
  text-align: center;
}
</style>
