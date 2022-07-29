<template>
  <AppWindow>
  tesy
  </AppWindow>
  <AppWindow>
  t
  </AppWindow>
</template>

<script>
import { defineComponent } from 'vue'

import AppWindow from './components/AppWindow.vue';

export default defineComponent({
  name: 'App',
  
  components: {
    AppWindow
  },

  setup() {
    /*const options = {
      title: 'Current count: 0',
      class: 'modern',
    };*/
    return {
      /*count,
      size,
      classObject,
      options,
      winboxRef,
      winboxRef2,*/
    }
  },
})
</script>

<style>

* {
  margin: 0;
  padding: 0;
}

#app {
  .modern {
    background-color: blue;
  }
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  //margin-top: 60px;
  height: 100vh;
}
</style>
