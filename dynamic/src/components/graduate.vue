<template>
    <div>
     <h1>I am {{ name }}, I have a degree in {{ course }} </h1>
     <input type="text" v-model="day">
    </div>
</template>

<script>
    export default {
        name:'GraduateComponent',
      props:['name','course'],
      data(){
        return{
            day:''
        }
      }
    }
</script>

<style scoped>

</style>