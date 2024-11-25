<template>
    <div>
<h1>this is a popup</h1>
<input type="text" v-model="name">
<button @click="$emit('close',name)">Hide</button>
    </div>
</template>

<script>
    export default {
        name:'PopupComponent',
        data(){
            return{
                name:'',
            }
        },
        
        emits:["close"]
    }
</script>

<style scoped>

</style>