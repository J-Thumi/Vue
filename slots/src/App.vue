<template>
 <SlotComponent />

 <SlotComponent>hello</SlotComponent>
  <SlotComponent>there</SlotComponent>
    <SlotComponent> i am</SlotComponent>
    <SlotComponent> 
      <template v-slot:header>
           <h1>i am the header</h1>
      </template>
      <template v-slot:default>
<h2>i am default</h2>
</template>
<template v-slot:footer>
<h1>footer here</h1>
</template>
    </SlotComponent>

   

    <NamesComponent>
      <template v-slot:default="slotProps">
       FULLNAME: {{ slotProps.firstname }} {{slotProps.lastname}}
        
      </template>

      <template v-slot:fnames="slotProps">
       FIRSTNAME: {{ slotProps.firstname }} 
        
      </template>
    </NamesComponent>
</template>

<script>
import SlotComponent from './components/slot'
import NamesComponent from './components/Names'
export default {
  name: 'App',
  components: {
    SlotComponent,
    NamesComponent
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
