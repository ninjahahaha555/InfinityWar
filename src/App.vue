<template>
  <div id="app">
    <HelloWorld msg="Infinity War Game" />   
    <CsButton label=""  />


  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import CsButton from "./components/CsButton.vue";
export default {
  name: "App",
  components: {
    HelloWorld,
    CsButton,
  },

  data: function () {
    return {
    min: 1,
    max: 10,
    number: 1,
    };
  },

  methods: {
    
  },
};
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
