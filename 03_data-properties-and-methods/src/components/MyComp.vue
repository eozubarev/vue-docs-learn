<template>
  <!-- Методы, вызываемые из шаблона, не должны иметь побочных эффектов -->
  <button @click="increment">Увеличить счётчик</button>
</template>


<script src="https://unpkg.com/lodash@4.17.20/lodash.min.js"></script>
<script>

/*
  В компоненте свойство data должно быть функцией. 
  Vue вызывает эту функцию на этапе создания нового экземпляра компонента.
*/

data() {
  return { 
    // свойства добавляются только при первом создании экземпляра,
    count: 4,
    something: null,
    something2: null
  }
},




/*
  Для добавления методов в экземпляр компонента используется опция methods. 
  Значением должен быть объект, который будет содержать все необходимые методы:
*/

methods: {
  increment() {
    // `this` указывает на экземпляр компонента
    this.count++
  }
},




/* 
  Реализация debounce и throttle
  Vue не предоставляет встроенной поддержки для debounce или throttle, но её легко можно реализовать 
  с помощью сторонних библиотек, например Lodash (opens new window).
*/

created() {
    // debounce с помощью Lodash
    this.debouncedClick = _.debounce(this.click, 500)
  },
  unmounted() {
    // Остановка таймера при уничтожении компонента
    this.debouncedClick.cancel()
  },
  methods: {
    click() {
      // ... обработка клика ...
    }
  },

</script>


<style scoped>
.read-the-docs {
  color: #888;
}
</style>
