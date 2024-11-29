<template>
    <div>
<button @click="increase">Click</button>
<h2>Clicked {{count}} times</h2>
    </div>
</template>

<script>
    export default {
        name:'ClickCounter',
        data(){
            return{
                count:0
            }
        },
        methods:{
            increase(){
                 this.count+=1
            }
        }
    }
</script>

<style scoped>

</style>