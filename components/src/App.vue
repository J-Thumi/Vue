<template>
  <div>
    <button @click="show=true">show</button>
    <PopupComponent v-show='show' @close="closePop"/>
    <button @click='popup=true'>open</button>
    <Popup2Component v-show="popup" @close="popup=false"/>
<GreetComponent name="Diana" hero="batman"/>
<GreetComponent name="Joan" hero="superman"/>
<GreetComponent :name="name" :hero="hero"/>
<ArticleComponent id="title" title="hello" :length="30" :isPublished="true"/>



<GreetComponent name="Joe" hero="Hulk"/>
</div>
</template>

<script>
import GreetComponent from './components/greet'
 import ArticleComponent from './components/article'
import PopupComponent from './components/Popup'
import Popup2Component from './components/popup2'

export default {
  name: 'App',
  data(){
    return {
      name:"Vishwas",
      hero:"Thanos",
      show:false,
      popup:false

    }
  },
  methods:{
    closePop(name){
      this.show=false
      console.log(`hello ${name}`)
    }
  },
  computed:{},
  watch:{},
  components:{
     GreetComponent,
   ArticleComponent,
    PopupComponent,
    Popup2Component
  },
  provide(){
    return {
      username: this.name
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
