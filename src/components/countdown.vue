<template>
    <div class="centered-container">
        <div>
    {{ countdown }}
    <div @click="start = !start; $emit('start')" id="start" v-if="!start">Start</div>
    <div @click="start = !start; $emit('stop')" id="stop" v-else>Stop</div>
    <div @click="_reset" id="reset">Reset</div>
</div>
    </div>
</template>

<script>
export default {
    data(){
        return {
            start:null
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
    name: 'Countdown',
    props: ['countdown','state']
}
</script>

<style>
.centered-container {
  display: flex;
  justify-content: center; /* Center horizontally */
  align-items: center; /* Center vertically */
}
#start{
    cursor: pointer;
}
#stop{
    cursor: pointer;
}
#gap{
    cursor: pointer;
}
</style>
