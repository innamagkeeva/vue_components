<script setup lang="ts">
import { computed, reactive, ref } from 'vue'
interface City {
  city: string
}

interface Hairstyles {
  title: string
  publishingHouse: string
  numberOfCopies: number
}

interface Color {
  color: string
}

const title = ref<string>('Отрисовка списков')
const cities = ref<City[]>([{ city: 'Москва' }, { city: 'Владикавказ' }])
const country = ref<string>('Россия')

const myHairstyles: Hairstyles = reactive({
  title: 'Техники стрижек',
  publishingHouse: 'Тренд',
  numberOfCopies: 500,
})
const colors = reactive<Color[]>([{ color: 'white' }, { color: 'blue' }, { color: 'yellow' }])

const animals = ref<string[]>(['тигр', 'кенгуру', 'лев', 'пингвин'])
const evenAnimals = computed(() => {
  return animals.value.filter((animal) => animal.length < 5)
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
    <p class="title">v-for и template</p>
    <ul>
      <template
        v-for="(color, index) in colors"
        :key="color"
      >
        <li>{{ color.color }}</li>
        <li
          v-if="index < colors.length - 1"
          class="divider"
          role="presentation"
        ></li>
      </template>
    </ul>
    <p
      class="title"
      style="padding: 0 30px"
    >
      Отображение отфильтрованных/отсортированных результатов
    </p>
    <ul>
      <li
        v-for="(animal, index) in evenAnimals"
        :key="animal"
      >
        {{ index }}- {{ animal }}
      </li>
    </ul>
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
  height: 910px;
  margin: 0 auto;
  margin-bottom: 10px;
  border: 3px solid greenyellow;
  padding: 10px 20px;
}

.divider {
  border-bottom: 1px solid black;
  margin-bottom: 10px;
}
</style>
