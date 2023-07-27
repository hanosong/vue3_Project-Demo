<script setup lang="ts">
  import { toRef, reactive } from 'vue';
  // toRef: 只能修改响应式对象的值，非响应式视图毫无变化；
  // 应用场景：用于响应式对象，单独操作某个属性 => 函数入参需要某个属性
  // 解决：使用reactive包裹对象
  // const man = {name: "haha", age: 24};
  const man = reactive({name: "haha", age: 24}); // 返回一个proxy对象
  const age = toRef(man, "age");

  const clickHandle = () => {
    age.value = 100;
    console.log(age.value, 'age') // 100
  }
</script>

<template>
  <div>
   {{man}}---
  </div>
  <div>
    toRef -- {{ age }}
  </div>
  <div>
    <button @click="clickHandle">修改信息</button>
  </div>
</template>

<style scoped>
</style>
