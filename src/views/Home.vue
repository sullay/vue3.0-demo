<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld :msg='msg' @update:msg="updateMsg"/>
    <h1 ref="root">{{x}}    {{y}}</h1>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import { useMousePosition } from '../hook/page.js'
import { ref, watchEffect, onMounted, getCurrentInstance } from 'vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  setup () {
    const root = ref(null)
    const currentInstance = getCurrentInstance()
    console.log(currentInstance)
    const { x, y } = useMousePosition()
    onMounted(() => {
      console.log(root)
    })
    const msg = ref('Welcome to Your Vue.js App')
    const updateMsg = (e) => {
      msg.value = e
    }
    watchEffect(() => {
      console.log(x.value, y.value)
    })
    return { msg, updateMsg, x, y, root }
  }
}
</script>
