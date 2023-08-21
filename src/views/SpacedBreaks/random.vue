<template>
    <div v-if="gapstate">
      <countdown :timer="currentTimer" />
      <div @click="timer" class="gapChanger">Timer</div>
    </div>
    <div v-else>
      <timer />
      <div @click="gap" class="gapChanger">Gap</div>
    </div>
  </template>
  
  <script>
  import Countdown from '@/components/spacedBreaksComponents/randomCountdown.vue';
  import Timer from '@/components/spacedBreaksComponents/randomTimer.vue';
  
  export default {
    data() {
      return {
        gapstate: false,
        currentTimer: 0, // Initial value
      };
    },
    methods: {
      gap() {
        console.log(this.currentTimer);
        this.gapstate = true;
      },
      timer() {
        this.gapstate = false;
        console.log(this.gapstate);
      }
    },
    components: {
      Countdown,
      Timer
    },
  }
  </script>
  
  <style>
  body {
    background-color: black;
  }
  
  h1 {
    color: white;
    margin-bottom: 0;
  }
  
  a {
    color: white;
  }
  
  .gapChanger {
    color: white;
    margin-top: 0;
    font-size: 2em;
    font-weight: bold;
    cursor: pointer;
  }
  </style>
  
