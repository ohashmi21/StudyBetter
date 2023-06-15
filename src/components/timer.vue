<template>
    <div>
    {{ timer }}
    <div @click="$emit('start')" id="start">Start</div>
    <div @click="$emit('stop')" id="stop">Stop</div>
    
    </div>
</template>

<script>
export default {
    name: 'Timer',
    props: ['timer','state']
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
