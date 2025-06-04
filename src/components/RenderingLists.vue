<script setup lang="ts">
import { reactive, ref } from 'vue'
interface City {
  city: string
}

interface Hairstyles {
  title: string
  publishingHouse: string
  numberOfCopies: number
}

const title = ref<string>('Отрисовка списков')
const cities = ref<City[]>([{ city: 'Москва' }, { city: 'Владикавказ' }])
const country = ref<string>('Россия')

const myHairstyles: Hairstyles = reactive({
  title: 'Техники стрижек',
  publishingHouse: 'Тренд',
  numberOfCopies: 500,
})
</script>

<template>
  <h1
    class="title"
    style="font-size: 40px"
  >
    {{ title }}
  </h1>
  <div class="circuit">
    <p class="title">Отображение элементов массива через v-for</p>
    <ul>
      <li
        v-for="city in cities"
        :key="city.city"
      >
        {{ city.city }}
      </li>
    </ul>
    <p class="title">второй опциональный параметр у v-for с индексом текущего элемента:</p>
    <ul>
      <li
        v-for="(city, index) in cities"
        :key="city.city"
      >
        {{ index }} : {{ country }} - {{ city.city }}
      </li>
    </ul>
    <p class="title">Отображение свойств объекта через v-for</p>
    <ul>
      <li
        v-for="value in myHairstyles"
        :key="value"
      >
        {{ value }}
      </li>
    </ul>
    <p
      class="title"
      style="font-size: 12px"
    >
      Второй аргумент для получения имени свойства (ключа объекта):
    </p>
    <ul>
      <li
        v-for="(value, key) in myHairstyles"
        :key="key"
      >
        {{ key }}: {{ value }}
      </li>
    </ul>
    <p
      class="title"
      style="font-size: 12px"
    >
      И третий — для индекса:
    </p>
    <ul>
      <li
        v-for="(value, key, index) in myHairstyles"
        :key="key"
      >
        {{ index }}. {{ key }}: {{ value }}
      </li>
    </ul>
    <p class="title">v-for и диапазоны</p>
    <span
      style="color: brown"
      v-for="n in 10"
      :key="n"
      >{{ n }}</span
    >
  </div>
</template>

<style scoped>
ul {
  margin-bottom: 20px;
  font-size: 20px;
}

.title {
  text-align: center;
  color: darkblue;
  font-size: 20px;
  margin-bottom: 10px;
}

.circuit {
  width: 500px;
  height: 900px;
  margin: 0 auto;
  margin-bottom: 10px;
  border: 3px solid greenyellow;
  padding: 10px 20px;
}
</style>
