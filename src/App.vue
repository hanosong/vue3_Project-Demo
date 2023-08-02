<script setup lang="ts">
  import { ref, computed } from 'vue';
  let firstName = ref("捞");
  let lastName = ref("工");
  // 1. 选项式写法，支持一个对象，传入get函数以及set函数自定义操作
  /* let name = computed<string> ({
    get(){
      return firstName.value + '-'+lastName.value
    },
    set(newName){
      [firstName.value, lastName.value] = newName.split('-')
    },
  })
  const clickHandle = () => {name.value = '小-哈'} */

  // 2.函数式写法：只能支持一个getter，不允许修改值
  let name = computed(() => firstName.value + '-' +lastName.value)

</script>

<template>
  <div>
   姓：<input v-model="firstName" type="text"/>
  </div>
  <div>
   名：<input v-model="lastName" type="text"/>
  </div>
  <div>
   全名：{{name }}
  </div>
  <div>
    <!-- <button @click="clickHandle">触发set</button> -->
  </div>
</template>

<style scoped>
</style>
