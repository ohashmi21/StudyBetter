//need to create components that have the configs for both the countdown and timer. Make it reactive and import the inputted time to the timer and countdown. 

<template>
    <div>
      <div><input v-model="CountdownLength" placeholder="edit me"/></div>
      
      <div>Stop</div>
      <div>Reset</div>
    </div>
</template>

<script>
  export default {
    data() {
      return {
        CountdownLength: 300,
        BreakMinimum: 1500,
        BreakMaximum: 1800,
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