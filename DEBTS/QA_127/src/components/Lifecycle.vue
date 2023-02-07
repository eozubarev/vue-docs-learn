<template>
  <h2>{{ info }}</h2>
  <button @click="change">change address</button>
</template>

<script setup lang="ts">
import { ref, watch } from 'vue'

const info = ref({
  name: 'evgeny',
  address: {
    street: 'any'
  }
})

// вотчер не отработает т.к меняется глубокое св-во объекта
// watch(info, (newValueCount, oldValueCount) => {
//   console.log('watch');
// })

// если добавляем deep true, то вотчер сработает
watch(info, (newValueCount, oldValueCount) => {
  console.log('watch');
}, { deep: true } )

const change = () => {
  info.value.address.street = 'pushkina'
}


</script>