<template>

  <ul id="array-rendering">
    <li v-for="item in items">
      {{ item.message }}
    </li>
  </ul>

  <!-- 1. Внутри блока v-for доступны все свойства из области видимости родителя.  -->
  <ul id="array-with-index">
    <li v-for="(item, index) in items">
      {{ parentMessage }} - {{ index }} - {{ item.message }}
    </li>
  </ul>



  <!-- 2. Отображение свойств объекта через v-for -->
  <ul id="v-for-object" class="demo">
    <li v-for="value in myObject">
      {{ value }}
    </li>
    <!-- Можно указать второй аргумент для получения имени свойства (ключа объекта): -->
    <li v-for="(value, name) in myObject">
      {{ name }}: {{ value }}
    </li>



  <!-- 3. Сохранение состояния -->
  <!-- 
        Чтобы подсказать Vue, как определять идентичность каждого элемента, и, таким образом, переиспользовать и упорядочивать 
        существующие элементы, необходимо указать уникальный атрибут key для каждого элемента: 
  -->
  <div v-for="item in items" :key="item.id">
    <!-- содержимое -->
  </div>



  <!-- 4. Отображение отфильтрованных/отсортированных результатов -->
  <li v-for="n in evenNumbers" :key="n">{{ n }}</li>



 <!-- 5. v-for и диапазоны -->
  <div id="range" class="demo">
    <span v-for="n in 10" :key="n">{{ n }}</span>
  </div>


 <!-- 6. не рекомендуется использовать вместе v-if и v-for.  -->
 <!-- Когда они указаны вместе на одном узле, у v-if будет больший приоритет, чем у v-for. И поэтому в условии v-if не будет доступа к переменным из области видимости v-for: -->

  <!-- Будет ошибка, так как свойство "todo" не объявлено в экземпляре. -->
  <li v-for="todo in todos" v-if="!todo.isComplete">
    {{ todo.name }}
  </li>

  <!-- Это можно исправить переместив v-for на тег-обёртку <template>: -->
  <template v-for="todo in todos" :key="todo.name">
    <li v-if="!todo.isComplete">
      {{ todo.name }}
    </li>
  </template>


  <!-- 7. v-for и компоненты -->
  <!-- Чтобы передать итерируемые данные в компонент потребуется явно использовать входные параметры: -->
  <my-component v-for="(item, index) in items"
                :item="item"
                :index="index"
                :key="item.id">
  </my-component>




  </ul>

</template>


<script>

data() {
    return {
      parentMessage: 'Родитель',
      items: [
        { message: 'Foo' },
        { message: 'Bar' }
      ],
      myObject: {
        title: 'How to do lists in Vue',
        author: 'Jane Doe',
        publishedAt: '2016-04-10'
      },
      numbers: [ 1, 2, 3, 4, 5 ],
    }
  },

computed: {
  evenNumbers() {
    return this.numbers.filter(number => number % 2 === 0)
  }
}

</script>


<style scoped>
.read-the-docs {
  color: #888;
}
</style>
