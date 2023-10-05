<template>
    <div>
      <h1>{{ formattedTime }}
        <Countdown 
          :timer="time" 
          :state="timerState" 
          @start="start"
          @stop="stop"
          @reset="reset"
        />
      </h1>
    </div>
  </template>
  
  <script>
  import Countdown from '@/components/countdown.vue';
  
  export default {
    name: 'CountdownTimer',
    components: {
      Countdown,
    },
    data() {
      return {
        timerState: "stopped",
        ticker: undefined,
        time: 5,
      }
    },
    computed: {
      formattedTime() {
        let measuredTime = new Date(null);
        measuredTime.setSeconds(this.time);
        let MHSTime = measuredTime.toISOString().substring(11, 19);
        return MHSTime;
      },
    },
    methods: {
      stop() {
        if (this.timerState === "running") {
          clearInterval(this.ticker);
          this.timerState = "stopped";
        }
      },  
      start() {
        if (this.timerState !== "running" && this.time !== 0) {
          this.tick();
          this.timerState = "running";
        }
      },
      tick() {
        this.ticker = setInterval(() => {
          this.time--;
          this.playalarm();
          if (this.time === 0){
            this.stop();
            this.time = 600;
          }
        }, 1000);
      },
      reset(){
        this.stop();
        this.time=1200;
      },
      playalarm(){
        var audio = new Audio(require("@/assets/keylimba_soft.mp3"))
        if (this.time==0){
          audio.play()
        }
      },
    }
  }
  </script>

  
  

