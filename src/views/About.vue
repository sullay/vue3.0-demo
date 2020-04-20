<template>
  <div class="about">
    <h1>{{name.name}}</h1>
    <h1>{{count}}</h1>
    <h1>{{computedCount}}</h1>
    <button @click="increamt">+</button>
  </div>
</template>

<script>
import { reactive, ref, computed, onMounted, watch } from 'vue'
export default {
  setup () {
    const name = reactive({
      name: 'hello xxx'
    })
    const count = ref(0)
    const increamt = () => {
      count.value++
    }
    const computedCount = computed(() => count.value * 100)
    onMounted(() => {
      console.log(name.name)
    })
    watch(count, (newVal, oldVal) => {
      console.log(newVal, oldVal)
    })
    return { name, count, increamt, computedCount }
  }
}
</script>
