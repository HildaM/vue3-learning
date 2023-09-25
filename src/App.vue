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

// 3. watch深度侦听
const state3 = ref({count: 0})
const changeStateByCount = () => {
  state3.value.count++
}

watch(state3, () => {
  console.log('深层watch：count变化了')
}, {
  deep: true
})

const state4 = ref({
  count: 0, 
  age: 22
})
const changeStateByCount2 = () => {
  state4.value.count++
}
// 精确侦听某个具体属性
watch(
  () => state4.value.age,   // 指明需要侦听的属性
  () => {
    console.log('age变化了')
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
  <div>
    <button @click="changeStateByCount">deep watch: count--{{ state3.count }}</button>
  </div>
  <div>
    <button @click="changeStateByCount2">deep watch2: count--{{ state3.count }}</button>
  </div>
</template>