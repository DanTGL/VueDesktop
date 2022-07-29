<template>
  <VueWinBox ref="winboxRef" :options="options" @onmove="onMove" @onresize="onResize">
    <div class="window" :class="classObject">
      <slot>
      </slot>
    </div>
  </VueWinBox>
</template>

<script>
import { defineComponent, ref, computed } from 'vue'
import VueWinBox from 'vue-winbox'

export default defineComponent({
  name: "AppWindow",
  components: { VueWinBox },
  setup() {
    const count = ref(0)
    const winSize = ref(0)

    const options = {
      title: 'Current count: 0',
      class: 'modern',
    }
    const winboxRef = ref()
    //const winboxRef2 = ref()

    const classObject = computed(() => {
      return {
        'sm': winSize.value >= 200,
        'md': winSize.value >= 500,
        'test': true,
      }
    });


    setInterval(() => {
      count.value++
      winboxRef.value?.winbox?.setTitle('Current count: ' + count.value)
      //console.log(winSize.value);
      //winboxRef2.value?.winbox?.setTitle('Current count: ' + count.value)
    }, 500)


    return {
      winSize,
      count,
      options,
      winboxRef,
      classObject,
      //winboxRef2,
      onMove({id}) {
          // id is the unique id of the window
          console.log(id);
      },
      onResize({id, width, height}) {
        console.log(id, height);
        winSize.value = width;
      }
    }
  }
})
</script>

<style>

.window {
  width: 100%;
  height: 100%;
  background-color: green;
}

.sm {
  background-color: red;
}

.md {
  background-color: blue;
}
</style>