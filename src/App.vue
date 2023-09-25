<script setup>
import { ref, watch } from 'vue';

// 1. 侦听单个数据的变化
const count = ref(0)
const setCount = () => {
  count.value++
}

// watch 侦听单个数据源
// 入参ref对象，不需要加value
watch(count, (newVal, oldVal) => {
  // 打印新值与旧值
  console.log('count变化了！', newVal, oldVal)
})


// 2. 同时侦听多个响应式数据的变化
const count2 = ref(0)
const changeCount = () => {
  count2.value++
}

const name = ref('cp')
const changeName = () => {
  name.value = 'pc'
}

// 同时侦听多个数据源
watch(
  [count2, name],
  ([newCount, newName], [oldCount, oldName]) => {
    console.log('count或者name变化了', [newCount, newName], [oldCount, oldName])
  }
)


</script>

<template>
  <div>
    <button @click="setCount">{{ count }}</button>
  </div>
  <div>
    <button @click="changeCount">修改count2--{{ count2 }}</button>
  </div>
  <div>
    <button @click="changeName">修改name--{{ name }}</button>
  </div>
</template>