<template>
    <div>
      <h1>
        <Timer 
          :timer="formattedTime" 
          :state="timerState" 
          @start="start"
          @stop="stop"
          @reset="reset"
        />
        <div @click="toggleModal" style="cursor:pointer;">Settings</div>
        <MyModal v-if="isModalVisible" @exit="exit" /> 
      </h1>
    </div>
  </template>
  
  <script>
  import MyModal from '@/components/spacedBreaksComponents/spacedBreakEditer.vue';
  import Timer from '@/components/timer.vue';
  function randomNumber(min, max) {
    return Math.round((Math.random() * (max - min)) / 60) * 60 + min;
  }  
  export default {
  name: 'randomTimer',
  components: {
    Timer,
    MyModal, // Register the MyModal component
  },
  data() {
    return {
      timerState: "stopped",
      currentTimer: null,
      formattedTime: "00:00:00",
      ticker: undefined,
      gapTimer: 0,
      gap: null,
      isModalVisible: false, // Initialize the modal visibility
    };
  },
    mounted() {
      this.gap = randomNumber((localStorage.getItem('min'))*60,(localStorage.getItem('max')*60));
      if (localStorage.currentTimer){
        this.currentTimer=localStorage.currentTimer;
        this.formattedTime=localStorage.formattedTime;
      }
    },
    methods: {
      stop() {
        if (this.timerState === "running") {
          clearInterval(this.ticker);
          this.timerState = "stopped";
          localStorage.currentTimer=this.currentTimer;
          localStorage.formattedTime=this.formattedTime;
        }
      },  
      start() {
        if (this.timerState !== "running") {
          this.tick();
          this.timerState = "running";
          console.log(this.gapTimer,this.gap)
        }
      },
      reset(){
        this.stop();
        this.currentTimer=0;
        this.gapTimer=0;
        this.formattedTime="00:00:00";
        localStorage.currentTimer=this.currentTimer;
          localStorage.formattedTime=this.formattedTime;
      },
      tick() {
        this.ticker = setInterval(() => {
          this.currentTimer++;
          this.gapTimer++;
          this.formattedTime = this.formatTime(this.currentTimer);
          this.gapChecker();
        }, 1000);
      },
      formatTime(seconds) {
        let measuredTime = new Date(null);
        measuredTime.setSeconds(seconds);
        let MHSTime = measuredTime.toISOString().substring(11, 19);
        return MHSTime;
      },
      playalarm(){
        var audio = new Audio(require("@/assets/keylimba_soft.mp3"))
        audio.play()
      },
      gapChecker() {
        if (this.gapTimer === this.gap) {
          this.playalarm();
          this.stop();
          this.gapTimer = 0;
          this.gap = randomNumber(600, 1800);
        }
      },
      toggleModal() {
      this.isModalVisible = !this.isModalVisible; // Toggle modal visibility
      console.log(this.isModalVisible)
      this.reset();
      },
      exit(){
        this.isModalVisible=!this.isModalVisible;
      },
    }
  }
  </script>
  
 
  