<script setup lang="ts">
import { ref } from 'vue'

type BasModifiers = 'stop' | 'prevent' | 'self' | 'capture' | 'once' | 'passive'
type BasKeyModifiers =
  | 'enter'
  | 'tab'
  | 'delete'
  | 'esc'
  | 'space'
  | 'up'
  | 'down'
  | 'left'
  | 'right'
type BasSystemKeyModifiers = 'ctrl' | 'alt' | 'shift' | 'meta'

const count = ref<number>(0)
const name = ref<string>('Влад')
const modifiers = ref<BasModifiers[]>(['stop', 'prevent', 'self', 'capture', 'once', 'passive'])
const keyModifiers = ref<BasKeyModifiers[]>([
  'enter',
  'tab',
  'delete',
  'esc',
  'space',
  'up',
  'down',
  'left',
  'right',
])
const systemKeModifiers = ref<BasSystemKeyModifiers[]>(['ctrl', 'alt', 'shift', 'meta'])

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
        v-for="(modifier, index) in modifiers"
        :key="modifier"
        :class="{ 'p-style': index === modifiers.length - 1 }"
      >
        . {{ modifier }}
      </li>
    </ul>
    <p class="title">Модификаторы клавиш. Псевдонимы клавиш</p>
    <ul>
      <li
        v-for="(keyModifier, index) in keyModifiers"
        :key="keyModifier"
        :class="{ 'p-style': index === keyModifiers.length - 1 }"
        style="color: darkred"
      >
        . {{ keyModifier }}
        <span
          v-if="keyModifier === 'delete'"
          style="color: brown; margin-left: 4px"
        >
          (ловит как «Delete», так и «Backspace»)</span
        >
      </li>
    </ul>
    <p class="title">Модификаторы системных клавиш</p>
    <p
      class="title"
      style="font-size: 15px"
    >
      модификаторы для прослушивания событий мыши или клавиатуры только при зажатой
      клавиши-модификатора:
    </p>
    <ul>
      <li
        v-for="(systemKeModifier, index) in systemKeModifiers"
        :key="systemKeModifier"
        :class="{ 'p-style': index === systemKeModifiers.length - 1 }"
        style="color: crimson"
      >
        .{{ systemKeModifier }}
      </li>
    </ul>
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
  height: 960px;
  margin: 0 auto;
  margin-bottom: 10px;
  border: 2px solid lightcoral;
  padding: 10px 20px;
}
</style>
