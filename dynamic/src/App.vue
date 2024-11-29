<template>
  <button @click="activeComp='GraduateComponent'">Graduate</button><br><br>
  <button @click="activeComp='UnderComponent'">Undergraduate</button>
  
  <!-- To keep dynamic components on the components alive 
   since every time a component is rendered an instance of it is created -->
<keep-alive>

  <component :is="activeComp" :name="name" :course="course"/>
</keep-alive>
<br>
<div v-if="loading">Loading...</div>
<!-- <div v-else>
  <div v-if="error">
    {{error}}
  </div>
  <div v-else>
  <PostsComponent :data="data"/></div>
</div> -->
<CreatePost />
<br>
<ClickCounter/>
</template>


<script>
import UnderComponent from './components/undergraduate'
import GraduateComponent from './components/graduate'
import PostsComponent from './components/posts'
import axios from 'axios'
import CreatePost from './components/createPost'
import ClickCounter from './components/Click'

export default {
  name: 'App',
  components: {
   UnderComponent,
   GraduateComponent,
   PostsComponent,
   CreatePost,
   ClickCounter
  },
  data(){
            return{
            name:'Josphat',
            course:'Computer Science',
            activeComp:'GraduateComponent',
            data:[],
            loading:true,
            error:''
        }
      },
      methods:{
       fetchData(){
        axios.get('https://jsonplaceholder.typicode.com/posts')
  .then((response)=>{
   console.log(response.data)
   this.data=response.data
   this.loading=false
  })
  .catch((err)=>{
    console.log(err)
     this.error='There is an error fetching'
     this.loading=false
  })
       }
      },
      mounted(){
   this.fetchData();
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
