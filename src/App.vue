<template>
  <AppWindow v-if="openApps[0]" :ref="'apps' + 0" @onclose="openApps[0]=false">
  <div class="w-full h-full sm-win:bg-blue-500 md-win:bg-black p-5">
    <div class="container mx-auto grid grid-cols-3 w-full">
      <div class="w-full h-32 bg-red-600">
      </div>
    </div>
  </div>
  </AppWindow>
  <AppWindow v-if="openApps[1]" :ref="'apps' + 1" @onclose="openApps[1]=false">
    <div class="grid md-win:grid-flow-row md-win:grid-cols-3">
      <div class="w-full h-32 bg-blue-600">
        
      </div>
      <div class="w-full h-32 bg-green-500">

      </div>

    </div>
  </AppWindow>

  <div class="flex flex-row place-content-center  absolute bottom-0 mx-auto w-full" id="taskbar">
    <div class="app border-2 place-self-end border-black bg-green-400 w-14 h-14 hover:w-20 hover:h-20 transition-all duration-150" v-for="(app, index) in openApps" @click="startApp(index)" :key="index" :class="app ? 'brightness-110' : ''">
      {{index}}
    </div>
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue'

import AppWindow from './components/AppWindow.vue';

export default defineComponent({
  name: 'App',
  
  components: {
    AppWindow
  },

  setup() {
        const openApps = ref([true, true])
    /*const options = {
      title: 'Current count: 0',
      class: 'modern',
    };*/

    /*const app1 = ref();
    const app2 = ref();*/
    setInterval(() => {
      /*openApps.value[0] = !openApps.value[0]
      openApps.value[1] = !openApps.value[1]*/
      //winboxRef.value?.winbox?.setTitle('Current count: ' + count.value)
      //console.log(winSize.value);
      //winboxRef2.value?.winbox?.setTitle('Current count: ' + count.value)
    }, 1000)


    return {
      openApps,
      /*count,
      size,
      classObject,
      options,
      winboxRef,
      winboxRef2,*/
      startApp(index) {
        if (openApps.value[index]) {
          this.$refs['apps' + index].winboxRef.winbox.focus();
        } else {
          openApps.value[index] = true;
        }
      },
    }
  },
})
</script>

<style>
body {
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
