<template>

  <div v-if="type === 'A'">
    A
  </div>
  <div v-else-if="type === 'B'">
    B
  </div>
  <div v-else-if="type === 'C'">
    C
  </div>
  <div v-else>
    Точно не A, B или C
  </div>
  

  <div v-if="Math.random() > 0.5">
      Сейчас меня видно
    </div>
    <div v-else>
      А теперь — нет
  </div>


  <h1 v-show="ok">Привет!</h1>

</template>

<template v-if="ok">
  <h1>Заголовок</h1>
  <p>Абзац 1</p>
  <p>Абзац 2</p>
</template>

<script>
</script>


<style scoped>
.read-the-docs {
  color: #888;
}
</style>
