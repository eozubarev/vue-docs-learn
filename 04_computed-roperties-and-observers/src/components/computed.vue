<template>
  <!-- 1 -->
  <div id="computed-basics" class="demo">
    <p>Has published books:</p>
      <span>{{ publishedBooksMessage }}</span>
  </div>



  <!-- 2 -->
  <p>{{ calculateBooksMessage() }}</p>


</template>


<script>

/* 1.
  В шаблоне к вычисляемым свойствам можно обращаться как и к обычным свойствам. Vue знает, что vm.publishedBooksMessage 
  зависит от значения vm.author.books, поэтому будет обновлять все привязки, которые зависят от vm.publishedBooksMessage, 
  при изменениях vm.author.books. И самая лучшая часть — эту зависимость создали декларативно: геттер-функция вычисляемого 
  свойства не имеет побочных эффектов, что облегчает понимание и тестирование.
*/

data() {
    return {
      author: {
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      }
    }
  },
  computed: {
    // a computed getter
    publishedBooksMessage() {
      // `this` points to the vm instance
      return this.author.books.length > 0 ? 'Yes' : 'No'
    }
  }




  // 2.
  //Кэширование вычисляемых свойств vs Методы
  /*
    Можно заметить, что того же результата можно достичь с помощью метода в выражении:
  */
  methods: {
    calculateBooksMessage() {
      return this.author.books.length > 0 ? 'Да' : 'Нет'
    }
  }
  /*
    Разница заключается в том, что вычисляемые свойства кэшируются на основе своих реактивных зависимостей. 
    Вычисляемое свойство будет пересчитываться только при изменении одной из своих зависимостей.
  */





  // 3.
  /*
    Сеттер вычисляемого свойства
    Вычисляемые свойства по умолчанию состоят только из геттера и поэтому доступны только для чтения. 
    Но при необходимости можно также определить и сеттер:
  */

  computed: {
    fullName: {
      // геттер (для получения значения)
      get() {
        return this.firstName + ' ' + this.lastName
      },
      // сеттер (при присвоении нового значения)
      set(newValue) {
        const names = newValue.split(' ')
        this.firstName = names[0]
        this.lastName = names[names.length - 1]
      }
    }
  }




  // 4.
  // Методы-наблюдатели





</script>


<style scoped>
.read-the-docs {
  color: #888;
}
</style>
