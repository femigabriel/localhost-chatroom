<template>
 <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/line-awesome/1.3.0/line-awesome/css/line-awesome.min.css"
  />

  <HelloWorld/>
  <!-- <Testing /> -->
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
// import Testing from './components/Testing.vue'


export default {
  name: 'App',
  components: {
    HelloWorld,
    // Testing
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
*{
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
  }
body {
    background: whitesmoke;
    color:#222;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
</style>
