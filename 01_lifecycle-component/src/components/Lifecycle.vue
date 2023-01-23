<template>
  
  <h1>Хуки жизненного цикла</h1>

  <div class="card">
    <div ref="el"></div>
    <button id="count" @click="count++">{{ count }}</button>
  </div>

</template>

<script setup>
import { ref, onMounted, onUpdated, onUnmounted } from 'vue'

// Монтирование компонента
const el = ref()
onMounted(() => {
  console.log(el.value)
})



// Обновление компонента
const count = ref(0)
onUpdated(() => {
  // text content should be the same as current `count.value`
  console.log(document.getElementById('count').textContent)
})



// Размонтирование компонента
let intervalId
onMounted(() => {
  intervalId = setInterval(() => {
    // ...
  })
})

onUnmounted(() => clearInterval(intervalId))

</script>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
