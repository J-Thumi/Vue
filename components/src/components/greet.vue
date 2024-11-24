<template>
    <div>
<h1>Hello {{name}} you are {{ hero }}</h1>
    </div>
</template>

<script>
    export default {
        name:'GreetComponent',
        props:['name',"hero"]
    }
</script>

<style scoped>

</style>