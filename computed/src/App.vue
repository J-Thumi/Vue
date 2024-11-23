<template>
  <h1>Volume regulation</h1>
  <h3>{{ volume }}</h3>
  <div>
    <button @click="increase">increase</button>
    <button @click="decrease">decrease</button>
  </div><br>
  <div>fullname {{ fullname }}</div>
  <div>firstname: {{ firstname }}</div>
  <div>lastname : {{ lastname }}</div>

  <input type="text" v-model="fullname">

  <div>{{ computedage }}</div>
  <div v-for="user in users" :key=user.name>
    <ul>
      <li>{{ user.name }}-{{user.age}}</li>
    </ul>
  </div>
  <div>{{ adults }}</div>
</template>

<script>


export default {
  name: 'App',
 data(){
  return{
volume:0,
users:[
  {
    name:"joe",
    age:6
  },
  {
    name:"john",
    age:78
  }
],
firstname:"Josphat",
lastname:"Thumi"
  }
 },
 methods:{
  increase(){
  return this.volume +=1
},
decrease(){
  return this.volume -=1
}
 },
 computed:{
computedage(){
  return this.users.reduce((total,user)=>total=total+user.age,0)
},
adults(){
   return this.users.filter(user=>user.age>18)
 
},


// fullname(){
// return `${this.firstname} ${this.lastname}`
// }

fullname:{
  get() {
        return `${this.firstname} ${this.lastname}`;
      },
      set(newValue) {
        const names = newValue.split('');
        this.firstname = names[0] || ''; // Fallback in case split fails
        this.lastname = names[1] || '';
  }
}
 },
 watch:{
volume(newvalue,oldvalue){
if(newvalue>oldvalue && newvalue==4){
  alert("high volume")
}}

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
