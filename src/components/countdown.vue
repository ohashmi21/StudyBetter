<template>
    <div>
    {{ countdown }}
    <div @click="$emit('start')" id="start">Start</div>
    <div @click="$emit('stop')" id="stop">Stop</div>
    </div>
</template>

<script>
export default {
    name: 'Countdown',
    props: ['countdown','state']
}
</script>

<style>
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
