<script setup lang="ts">
  const arr:string[] = ['nba', 'cba', 'aaa']
</script>

<template>
  <div v-for="(item, index) in arr">
    {{ item }} - {{ index }}
  </div>
</template>

<style scoped>
</style>
