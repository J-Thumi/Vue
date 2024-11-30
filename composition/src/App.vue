<template>
  <h1>{{ f_name }}</h1>
  <h2>{{greet}}</h2>
  <h3>Reactive:{{ reactGreet }}</h3>

  <ReactivityComponent :sname="count" :bname="age"/>

  <h1>{{count}}</h1>
  <button @click="increase">Increase</button>

  <h1>{{ sname }} {{ bname }}</h1>
  <button @click="ChangeName">Change Name</button>
  <br><br>
<input type="text" placeholder="work" v-model="work">
<input type="text" placeholder="workk" v-model="workk">
<input type="text" placeholder="title" v-model="title">
<input type="text" placeholder="pages" v-model="pages">
<input type="text" placeholder="main  author" v-model="author.main">
<h1>{{ sentence }}</h1>
</template>

<script>
import {ref, reactive,toRefs, computed,watch,provide} from 'vue'
import ReactivityComponent from './components/reactivity'
import _ from 'lodash'
export default {
  name: 'App',
  components:{
    ReactivityComponent
  },
  setup(){
    // Replacing data(){}
    const f_name=ref('John')
    const l_name=ref('Bee')
    const hero= ref('Batman')
    
    f_name.value='Diana'

    const greet=`Hello ${f_name.value} ${l_name.value} you are ${hero.value}`

// Repeatition should be avoided hence use reactive
    const state=reactive({
      fname:'Diana',
      lname:'Bee',
      hero:'Wonder Woman'

    })
const reactGreet=`Hello ${state.fname} ${state.lname} you are ${state.hero}`

    //Replacing methods using ref
    const count=ref(0)
    function increase(){
       count.value++
    }

    //replace methods using reactive and toREfs

    const fname=reactive({
      sname:'Doe',
      bname:'Jimmy'

    })
    function ChangeName(){
      fname.sname='Coach',
      fname.bname='Cater'
    }

    //replacing v-model
    const work=ref('')
    const Book=reactive({
      title:'',
      pages:'',
      author:{
        main:''
      }
    })

    //computed properties
   const sentence= computed(function(){
      return `${Book.title} has ${Book.pages} pages and is about ${work.value}`
    })
     
    //replacing watchers using ref
    watch(count,(pre,post)=>{
     if(pre==4 && pre>post){
        console.log('max volume')
     }
    })

    const workk=ref('')
    watch([work,workk],(prevalues,pastvalues)=>{
      console.log(`work ${prevalues[0]}`)
      console.log(`past work ${pastvalues[0]}`)
      console.log(`work 2 ${prevalues[1]}`)
      console.log(`past work 2 ${pastvalues[1]}`)
    },{
      immediate:true
    })

    //watchers in reactive
    watch(
      ()=>{
        //by default the watcher in reactive the past and present are same to prevent this use an arrow function with the variable to watch being returned in spread
        //also if you want to watch only on eof the variables in reactive use an arrow function
       // ()=>Book.title 
        return {...Book}
      },(pre,past)=>{
      console.log(`title ${pre.title}`)
      console.log(`title ${past.title}`)
      console.log(`pages ${pre.pages}`)
      console.log(`pages ${past.pages}`)

    })

    //nested using deep watchers
    watch(
      ()=>_.cloneDeep(Book.author),

  (pre,past)=>{
    console.log(pre)
    console.log(past)
  },

  {deep:true}
  //you will note pre and past are similar to change  this we can use lodash _.cloneDeep in the first fn
)
//provide and inject
const age=ref(89)
const phone=reactive({
  imei:'rtdty456',
  color:'blue'
})
provide('from','parent')
provide('age',age)
provide('phone',phone)



    return{
      f_name,
      l_name,
      hero,
      greet,
      reactGreet,
      state,
      count,
      increase,
      ...toRefs(fname),
      ChangeName,
      work,
      ...toRefs(Book),
      sentence,
      workk,
      age,
      ...toRefs(phone)

    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
