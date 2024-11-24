<template>
    <div>
<h1 v-bind="$attrs">{{ title }}</h1>
<h1>{{ length }}</h1>
<h1>{{ isPublished ? "yes" : "no" }}</h1>
    </div>
</template>

<script>
    export default {
        name:"ArticleComponent",
        props:{
            title:{
                type:String,
                required:true,
                default:"article title"
            },
            length:Number,
            isPublished:Boolean
        },
        inheritAttrs:false
    }
</script>

<style scoped>

</style>