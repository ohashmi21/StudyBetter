<template>
    <div>
      {{ timer }}
      <div @click="start = !start; $emit('start')" id="start" v-if="!start">Start</div>
      <div @click="start = !start; $emit('stop')" id="stop" v-else>Stop</div>
      <div @click="_reset" id="reset">Reset</div>
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
  #start,
  #stop,
  #reset {
    cursor: pointer;
  }
  </style>
  