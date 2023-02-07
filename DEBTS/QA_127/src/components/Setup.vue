<script setup lang="ts">
/* Setup это синтаксический сахар для использования Composition API внутри однофайловых компонентов (SFC)
   код внутри компилируется как содержимое функции setup()
   в отличии от обычного <script>, который выполняется только 1 раз при первом импорте компонента, 
   код внутри setup будет выполнятся каждый раз, при создании экземпляра компонента
*/

// Мы можем легко испортировать различные вспомогательные фун-и не разворачивая их в через опцию методов
import { capitalize } from './helpers'


const msg: string = 'Hello!'

const printAny = () => {
    console.log(msg)
}

</script>

<template>
  <button @click="printAny">{{ msg }}</button>
  <div>{{ capitalize('hello') }}</div>
</template>
