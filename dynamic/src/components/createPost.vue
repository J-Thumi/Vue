<template>
    <div>
        <form @submit.prevent="submitHandler">
            <div>
        <label for="title">Title</label>
    <input type="text" v-model="formData.title" ref="title">
</div>
    <div>
    <label for="body">body</label>
    <input type="text" v-model="formData.body" >
</div>
    <input type="submit" value="Submit">
</form>
    </div>
</template>

<script>
import axios from 'axios';

    export default {
        name:"CreatePost",
        data(){
            return{
            formData:{
                 title:'',
                 body:""
            }
        }
        },
        methods:{
            submitHandler(){
                axios.post('https://jsonplaceholder.typicode.com/posts',this.formData)
                .then((response)=>console.log(response))
                .catch((err)=>console.log(err))
            }
        },
        mounted(){
            this.$refs.title.focus()
        }
    }
</script>

<style scoped>

</style>