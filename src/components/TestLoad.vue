<script setup>
import {shallowRef, customRef} from "vue";

const value = shallowRef({
  name: '触发'
})

const change = () => {
  // 以下不会触发
  value.value.name = '不触发'
  // 以下会触发
  value.value = {
    name: '触发了'
  }
}

const myRef = (value) => {
  let timer
  return customRef((track, trigger) => {
    return {
      get() {
        track() // 收集依赖
        return value
      },
      set(newVal) {
        clearTimeout(timer)
        timer = setTimeout(() => {
          console.log('触发了')
          value = newVal
          timer = null
          trigger() // 触发
        },1000)
      }
    }
  })
}

const obj = myRef('测试1')
const changeMyRef = () => {
  obj.value = '测试2'
}
</script>

<template>
  <div>
    {{ obj }}
    <button @click="changeMyRef">Click Me</button>
  </div>
</template>

<style scoped>

</style>