<template>
    <div>
        <h1 v-for="name in names" :key="name.firstname">
         <slot :firstname="name.firstname" :lastname="name.lastname"> </slot>
         <br>  
         <slot name="fnames" :firstname="name.firstname"></slot>    
         </h1>

    </div>
</template>

<script>
    export default {
        name:'NamesComponent',
        data(){
            return {
            names:[
  { firstname: "John", lastname: "Doe" },
  { firstname: "Jane", lastname: "Smith" },
  { firstname: "Alice", lastname: "Johnson" }
]
        }
    }}
</script>

<style scoped>

</style>