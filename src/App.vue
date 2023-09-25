<script setup>
// reactive对象
// 1. 导入函数
import { reactive } from 'vue';
// 2. 执行对象
// reactive只接收‘对象类型’的参数。如果是简单类型，需要用ref
const state = reactive({
  count: 0
})
const setCount = () => {
  state.count++
}

// ref对象
import { ref } from 'vue';
// [简单类型 + 对象类型]
const count = ref(0)
const setCount2 = () => {
  // 脚本区域修改ref的数据，必须通过 .value 属性修改
  count.value++
}

</script>

<template>
  <div>
    <button @click="setCount">{{ state.count }}</button>
    <button @click="setCount2">{{ count }}</button>
  </div>
</template>