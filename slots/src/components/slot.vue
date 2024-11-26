<template>
    <div>
<slot>heyeeyyy</slot>
<div>
    <slot  name="footer"></slot>
</div>
<div >
    <slot name='header'></slot>
</div>
<div >
    <!-- you can leave one unamed slot -->
    <slot></slot>
</div>

    </div>
</template>

<script>
    export default {
        name:'SlotComponent',
        props:['content']
    }
</script>

<style scoped>

</style>