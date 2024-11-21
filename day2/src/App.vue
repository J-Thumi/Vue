<template>
  <div v-for="name in names" :key="name">{{name}}</div><br>
 <div v-for="(index,name) in names" :key="name">{{index}} {{name}}</div> <br>
 <div v-for="(names,index) in fullnames" :key="names.first">{{index+1}} {{names.first}} {{names.last}}</div>
 <div v-for="actor in actors" :key="actor.name">
<h1>{{actor.name}}:</h1>
<h4 v-for="movie in actor.movies" :key="movie">{{movie}}</h4>
 </div>
<h1>Addition</h1>
 <div>{{add(1,2,3)}}</div>
 <h1>Multiply</h1>
 <div>{{multiply(number)}}</div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return{ names:["joe","wawesh","john","doe"],
  fullnames:[
    {first:"joe",last:"wawesh"},
    {first:"joe",last:"wawesh"},
    {first:"joe",last:"wawesh"},
  ],
  actors:[
    {
      name:"dwayne johnson",
      movies:["moana","first five"]
    },
    {
      name:"kevin hart",
      movies:['ready or nor','die hard']
    }
  ],
  number:7
  }
  
  },
  methods:{
    add(a,b,c){
      return a+b+c
    },
    multiply(num){
      return num*this.number
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
