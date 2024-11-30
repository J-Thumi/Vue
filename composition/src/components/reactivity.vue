<template>
    <div>
     <h1>{{user.fname}}</h1>
     <h1>{{product}}</h1>
     <h1>{{quantity}}</h1>
     <h1>{{child}}</h1>
     <h1>{{ age }}</h1>
     <h1>{{imei}}</h1>
     <h1>{{ color }}</h1>
     <h1>{{full}}</h1>
     <!-- color and imei injected from phone in app.vue -->
    </div>
</template>

<script>
import {reactive,toRefs,inject , computed} from 'vue'

    export default {
        name:'ReactivityComponent',
        setup(props){
            //using reactive and ref the dom can change on setTimeout but using const direct it do not change
           const user= reactive({
                fname:'Diana',
      lname:'Bee',
      hero:'Wonder Woman'
            })
       setTimeout(()=>{
        user.fname='John'
       },4000)

    //    it is working but in order to access the fname in template i always will user user.fname which may be tidious

     const order=reactive({
        product:'Oraimo',
        quantity:45
     })

     // if i try to use setTimeout it will not work untill i introduce toRefs
     setTimeout(()=>{
        order.product='Buds'
     },4000)
   
const child=inject('from','Default')
const age=inject('age',0)
const phone=inject('phone',{})

const full=computed(()=>{
    return `${props.sname} ${props.bname}`
})
            return{
                user,
                //to avoid always using order.product
                ...toRefs(order),
                child , //injected from app.vue
                age,
                ...toRefs(phone),
                full
            }
        },
        //props in composition must be declared explicitly then passed to setup as arg
        props:['sname','bname']
    }
</script>

<style scoped>

</style>