<script setup lang="ts">
import { ref } from 'vue'

const count = ref<number>(0)
const name = ref<string>('Влад')

function greet(event: Event): void {
  console.log(`Привет ${name.value} !`)
  if (event) {
    console.log((event.target as HTMLInputElement).value) // Вот этот консоль.лог - написано в документации но не понятно для чего он нужен бывает.
  }
}
</script>
<template>
  <h1
    class="title"
    style="font-size: 40px"
  >
    Обработка событий
  </h1>
  <div class="circuit">
    <p class="title">Обработчик события в виде инлайн-кода</p>
    <p class="p-style">Обычно подобный подход используют лишь в очень простых случаях, например:</p>

    <button @click="count++">Добавить 1</button>

    <button @click="count--">Убрать 1</button>
    <p style="margin-bottom: 20px">{{ count }}</p>
    <p class="title">Обработчик события в виде метода</p>
    <p class="p-style">v-on также принимает имя метода, который потребуется вызвать.</p>
    <button @click="greet">Приветствовать</button>
  </div>
</template>
<style scoped>
.p-style {
  margin-bottom: 10px;
}

.title {
  text-align: center;
  color: rebeccapurple;
  font-size: 20px;
  margin-bottom: 10px;
}

.circuit {
  width: 500px;
  height: 910px;
  margin: 0 auto;
  margin-bottom: 10px;
  border: 2px solid lightcoral;
  padding: 10px 20px;
}
</style>
