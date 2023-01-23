<template>

  <!-- Интерполяции -->
  <span>Сообщение: {{ msg }}</span>


  <!-- Сырой HTML -->
  <p>Двойные фигурные скобки: {{ rawHtml }}</p>
  <p>Директива v-html: <span v-html="rawHtml"></span></p>



  <!-- Атрибуты / Синтаксис двойных фигурных скобок нельзя использовать внутри HTML-атрибутов. -->
  <button v-bind:disabled="isButtonDisabled">Кнопка</button>



  <!-- Использование выражений JavaScript -->
  {{ number + 1 }}

  {{ ok ? 'YES' : 'NO' }}

  {{ message.split('').reverse().join('') }}

  <div v-bind:id="'list-' + id"></div>


  <!-- Директивы / специальные атрибуты с префиксом v --->
  <!-- Задачей директивы является реактивное применение изменений к DOM, когда изменится значение выражения. -->
  <p v-if="seen">Сейчас меня видно</p>


  <!-- Аргументы -->
  <!-- Некоторые директивы могут принимать «аргумент», отделяемый двоеточием от названия директивы. -->
  <a v-bind:href="url"> ... </a>

  <!-- Другим примером может быть директива v-on, которая отслеживает события DOM: -->
  <a v-on:click="doSomething"> ... </a>



  <!-- Модификаторы -->
  <form v-on:submit.prevent="onSubmit">...</form>
  


  <!-- Сокращённая запись / Сокращение v-bind -->
  <a :href="url"> ... </a>
  <a :[key]="url"> ... </a>

  <!-- Сокращение v-on -->
  <a @click="doSomething"> ... </a>
  <a @[event]="doSomething"> ... </a>



</template>

<script>

const msg = 'Какой-то текст';
const rawHtml: '<span style="color: red">This should be red.</span>';
const isButtonDisabled = null;

let number = 0
const ok = 'NO';
const message = 'тевирп'
const id = 1;

const seen = false;
const url = 'https://calendar.google.com';
const doSomething = () => return 'doSomething'

const onSubmit = () => return 'onSubmit'


</script>


<style scoped>
.read-the-docs {
  color: #888;
}
</style>
