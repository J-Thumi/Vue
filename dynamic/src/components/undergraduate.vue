<template>
    <div>
        
       <h1>I am {{name}} ,an undergraduate pursuing {{ course }}</h1>
    </div>
</template>

<script>
    export default {
        name:'UnderComponent',
        props:['name','course']
        }
   
</script>

<style scoped>

</style>