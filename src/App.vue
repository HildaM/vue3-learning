<script setup>
import { onMounted, ref } from 'vue';

// 1. 调用ref函数 --> ref对象
const h1Ref = ref(null)
const button1 = ref(null)

// 组件挂载完毕后才能获取
onMounted(() => {
  console.log(h1Ref.value)
})
onMounted(() => {
  if (button1.value) {
    console.log('获取button成功')
  } else {
    console.log('未点击button，无法获取')
  }
})

</script>

<template>
  <!-- 2. 通过 ref 标识绑定 ref 对象 -->
  <h1 ref="h1Ref">
    我是dom标签1
  </h1>
</template>