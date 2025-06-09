<script setup lang="ts">
import { ref } from 'vue'

type BasModifiers = 'stop' | 'prevent' | 'self' | 'capture' | 'once' | 'passive'

const count = ref<number>(0)
const name = ref<string>('Влад')
const modifiers = ref<BasModifiers[]>(['stop', 'prevent', 'self', 'capture', 'once', 'passive'])

function greet(event: Event): void {
  console.log(`Привет ${name.value} !`)
  if (event) {
    console.log((event.target as HTMLInputElement).value) // Вот этот консоль.лог - написано в документации но не понятно для чего он нужен бывает.
  }
}

function say(message: string): void {
  console.log(message)
}

function warn(message: string, event: Event): void {
  if (event) {
    event.preventDefault()
  }
  console.log(message)
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
    <button
      @click="count++"
      style="margin-right: 10px"
    >
      Добавить 1
    </button>
    <button @click="count--">Убрать 1</button>
    <p
      class="p-style"
      style="color: red; font-size: 30px"
    >
      {{ count }}
    </p>
    <p class="title">Обработчик события в виде метода</p>
    <p class="p-style">v-on также принимает имя метода, который потребуется вызвать.</p>
    <button
      class="p-style"
      @click="greet"
    >
      Приветствовать
    </button>
    <p class="title">Вызов методов в инлайн-обработчиках</p>
    <button
      @click="say('привет!')"
      style="margin: 0 10px 20px; color: green"
    >
      Привет!
    </button>
    <button
      @click="say('пока!')"
      style="color: blueviolet"
    >
      Пока!
    </button>
    <p class="title">Доступ к событию через аргумент в инлайн-обработчиках</p>
    <button
      class="p-style"
      @click="warn('пока нельзя отправить', $event)"
    >
      отправить
    </button>
    <p class="title">Модификаторы событий</p>
    <ul>
      <li
        v-for="modifier in modifiers"
        :key="modifier"
      >
        . {{ modifier }}
      </li>
    </ul>
  </div>
</template>

<style>
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
