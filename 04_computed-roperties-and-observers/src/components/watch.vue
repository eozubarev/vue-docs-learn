<template>
  <div id="demo">{{ fullName }}</div>
</template>

<!-- Поскольку уже существует обширная экосистема ajax-библиотек -->
<!-- и библиотек функций общего назначения, ядро Vue может       -->
<!-- оставаться маленьким и не изобретать их заново. Кроме того, -->
<!-- это позволяет использовать только знакомые инструменты.     -->

<script src="https://cdn.jsdelivr.net/npm/axios@0.12.0/dist/axios.min.js"></script>
<script>

  // 1

  const watchExampleVM = Vue.createApp({
    data() {
      return {
        question: '',
        answer: 'Вопросы обычно заканчиваются вопросительным знаком. ;-)'
      }
    },
    watch: {
      // при каждом изменении `question` эта функция будет запускаться
      question(newQuestion, oldQuestion) {
        if (newQuestion.indexOf('?') > -1) {
          this.getAnswer()
        }
      }
    },
    methods: {
      getAnswer() {
        this.answer = 'Думаю...'
        axios
          .get('https://yesno.wtf/api')
          .then(response => {
            this.answer = response.data.answer
          })
          .catch(error => {
            this.answer = 'Ошибка! Нет доступа к API. ' + error
          })
      }
    }
  }).mount('#watch-example')



  // 2
  /*
    Чаще всего уместнее использовать вычисляемые свойства, чем вызовы методов-наблюдателей watch.
  */

  const vm = Vue.createApp({
    data() {
      return {
        firstName: 'Foo',
        lastName: 'Bar',
        fullName: 'Foo Bar'
      }
    },
    watch: {
      firstName(val) {
        this.fullName = val + ' ' + this.lastName
      },
      lastName(val) {
        this.fullName = this.firstName + ' ' + val
      }
    }
  }).mount('#demo')

  // Код выше является императивным и повторяющимся. Сравним с вычисляемым свойством:

  const vm = Vue.createApp({
    data() {
      return {
        firstName: 'Foo',
        lastName: 'Bar'
      }
    },
    computed: {
      fullName() {
        return this.firstName + ' ' + this.lastName
      }
    }
  }).mount('#demo')



</script>


<style scoped>
.read-the-docs {
  color: #888;
}
</style>
