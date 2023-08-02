<script setup lang="ts">
import { ref, watchEffect } from 'vue';

 let message1 = ref<string>("初始化数据1");
 let message2 = ref<string>("初始化数据2");

 // 数据发生变化时触发，默认初始化时会执行一次
 // 返回一个停止监听的函数
  const stop = watchEffect((oninvalidate) => {
    console.log(message1.value, "message1");
    console.log(message2.value, "message2");
    let _div:HTMLElement = document.querySelector('#mydiv') as HTMLDivElement;
    console.log(_div, "divvvvv"); // <div id="mydiv"></div>
    oninvalidate(() => {
      // 所有数据变化之前执行的构造 => 用于清除接口。。。
      console.log("succ~~");
    })
  },{
    flush: "post", // 当dom挂载完毕之后，开始监听
    // 用于调试的api
    // onTrigger(e){
    //   debugger; 
    // }
  })

  const stopWatchHandle = () => stop();
</script>

<template>
  <div>
    <input type="text" v-model="message1"/>
  </div>
  <div>
    <input type="text" v-model="message2"/>
  </div>
  <div id="mydiv"></div>
  <div>
    <button @click="stopWatchHandle">停止对数据进行监听！！</button>
  </div>
</template>

<style scoped>
</style>
