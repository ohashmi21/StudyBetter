<template>
    <div>
      <h1>
        <Timer 
          :timer="formattedTime" 
          :state="timerState" 
          @start="start"
          @stop="stop"
        />
      </h1>
    </div>
  </template>
  
  <script>
  import Timer from '@/components/timer.vue';
  
  function randomNumber(min, max) {
    return Math.round((Math.random() * (max - min)) / 60) * 60 + min;
  }
  
  export default {
    name: 'randomTimer',
    components: {
      Timer,
    },
    data() {
      return {
        timerState: "stopped",
        currentTimer: 0,
        formattedTime: "00:00:00",
        ticker: undefined,
        gapTimer: 0,
        gap: 0,
      }
    },
    mounted() {
      this.gap = randomNumber(900, 1800);
    },
    methods: {
      stop() {
        if (this.timerState === "running") {
          clearInterval(this.ticker);
          this.timerState = "stopped";
        }
      },  
      start() {
        if (this.timerState !== "running") {
          this.tick();
          this.timerState = "running";
        }
      },
      tick() {
        this.ticker = setInterval(() => {
          this.currentTimer++;
          this.gapTimer++;
          this.formattedTime = this.formatTime(this.currentTimer);
          console.log(this.currentTimer)
          this.gapChecker();
        }, 1);
      },
      formatTime(seconds) {
        let measuredTime = new Date(null);
        measuredTime.setSeconds(seconds);
        let MHSTime = measuredTime.toISOString().substring(11, 19);
        return MHSTime;
      },
      gapChecker() {
        if (this.gapTimer === this.gap) {
          this.stop();
          this.gapTimer = 0;
          this.gap = randomNumber(600, 1800);
        }
      },
    }
  }
  </script>
  
 
  