<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld :msg='msg' @update:msg="updateMsg"/>
    <h1>{{x}}    {{y}}</h1>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import { useMousePosition } from '../hook/page.js'
import { ref } from 'vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  setup () {
    const { x, y } = useMousePosition()
    const msg = ref('Welcome to Your Vue.js App')
    const updateMsg = (e) => {
      msg.value = e
    }
    return { msg, updateMsg, x, y }
  }
}
</script>
