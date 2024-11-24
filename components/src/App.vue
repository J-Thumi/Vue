<template>
  <div>
<GreetComponent name="Joe" hero="Hulk"/>
<GreetComponent name="Diana" hero="batman"/>
<GreetComponent name="Joan" hero="superman"/>
<GreetComponent :name="name" :hero="hero"/>
<ArticleComponent id="title" title="hello" :length="30" :isPublished="true"/>
</div>
</template>

<script>
import GreetComponent from './components/greet'
import ArticleComponent from './components/article'

export default {
  name: 'App',
  data(){
    return {
      name:"Vishwas",
      hero:"Thanos"

    }
  },
  methods:{},
  computed:{},
  watch:{},
  components:{
    GreetComponent,
    ArticleComponent
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
