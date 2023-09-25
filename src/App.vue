<script setup>
import { ref, computed } from 'vue';

const list = ref(
  [1, 2, 3, 4, 5, 6 ,7 ,8 ]
)
const computedList = computed(() => {
  // 根据一个数据得到一个新数据，除此之外的功能都是“副作用”
  return list.value.filter(item => item > 2)
})

setTimeout(() => {
  list.value.push(9, 10)
}, 3000)

</script>

<template>
  <div>
    原始数组：{{ list }}
  </div>
  <div>
    computed后的数组：{{ computedList }}
  </div>
</template>