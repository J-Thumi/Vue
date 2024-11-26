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
</template>

<script>
import SlotComponent from './components/slot'

export default {
  name: 'App',
  components: {
    SlotComponent
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
