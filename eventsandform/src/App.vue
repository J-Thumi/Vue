<template>
  <div>
    <h1>{{ name }}</h1>
    <button @click="changeName, increment(1)">change name</button>
    <h1>{{ count }}</h1>
    <button @click="increment(1)">increment by 1</button>
    <button @click="decrement(1)">decrease by 1</button>
    <br>
    <button v-on:click="increment(5)">increase by 5</button>
    <button v-on:click="decrement(5)">decrease by 5</button>
  </div>
<pre>
  {{ JSON.stringify(inputField, null,2) }}
</pre>
<form @submit="submitForm">

  <label for="name">Name:</label>
  <input type="text" id="name" v-model="inputField.name"><br><br>

  <label for="summary">summary : </label>
  <textarea v-model="inputField.summary" id="summary"></textarea><br><br>

  <label for="country">country</label>
  <select id="country" v-model="inputField.country">
    <option value="Kenya">Kenya</option>
    <option value="uganda">uganda</option>
    <option value="tanzania">tanzania</option>
    <option value="somalia">somalia</option>
  </select><br><br>

  <label for="favorite">favorite</label>
  <select id="favorite" multiple v-model="inputField.favorite">
    <option value="Kenya">Kenya</option>
    <option value="uganda">uganda</option>
    <option value="tanzania">tanzania</option>
    <option value="somalia">somalia</option>
  </select><br><br>

  <input type="checkbox" id='work' v-model="inputField.openToWork" true-value="yes" false-value="no">
  <label for="work">Open to work?</label><br><br>


  <fieldset >
    <label for="units">units</label> <br>
    <input type="checkbox" value="english" id="units" v-model="inputField.units">english <br>
    <input type="checkbox" value="kiswahili" id="units" v-model="inputField.units"> kiswahili <br>
    <input type="checkbox" value="chem" id="units" v-model="inputField.units"> chem <br>
  </fieldset>

  
  <fieldset >
    <label for="years">years of experience</label> <br>
    <input type="radio" value="1-4" id="years" v-model="inputField.years">1-4 <br>
    <input type="radio" value="5-7" id="years" v-model="inputField.years"> 5-7 <br>
    <input type="radio" value="8-10" id="years" v-model="inputField.years"> 8-10<br>
  </fieldset>

  <button>Submit</button>
</form>
</template>

<script>


export default {
  name: 'App',
  data(){
    return {
     name:"joe",
     count:0,
     inputField:{
      name:'',
      summary:'',
      country:'',
      favorite:[],
      units:[],
      openToWork:true,
      years:''
     }
    }
  },
  methods:{
    changeName(){
      this.name="joee"
      
    },
    increment(num){
      this.count+=num
     
    },
    decrement(num){
      this.count-=num
      
    },
    submitForm(event){
      event.preventDefault()
      console.log('form details', this.inputField)
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
