<template>
    <div>
<h1>i am pop up 2</h1>
<button @click="$emit('close')">close</button>
    </div>
</template>

<script>
    export default {
        name:"Popup2Component",
        emit:['close']
    }
</script>

<style scoped>

</style>