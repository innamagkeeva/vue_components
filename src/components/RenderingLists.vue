<script setup lang="ts">
import { ref } from 'vue'
interface City {
  city: string
}

const title = ref<string>('Отрисовка списков')
const cities = ref<City[]>([{ city: 'Москва' }, { city: 'Владикавказ' }])
const country = ref<string>('Россия')
</script>

<template>
  <h1 class="title">{{ title }}</h1>
  <div class="circuit">
    <p
      class="title"
      style="font-size: 20px"
    >
      Отображение элементов массива через v-for
    </p>
    <ul>
      <li
        v-for="city in cities"
        :key="city.city"
      >
        {{ city.city }}
      </li>
    </ul>
    <p
      class="title"
      style="font-size: 18px"
    >
      второй опциональный параметр у v-for с индексом текущего элемента:
    </p>
    <ul>
      <li
        v-for="(city, index) in cities"
        :key="city.city"
      >
        {{ index }} : {{ country }} - {{ city.city }}
      </li>
    </ul>

    <p style="color: brown">Продолжение следует))))))))......</p>
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
  font-size: 40px;
  margin-bottom: 10px;
}

.circuit {
  width: 500px;
  height: 400px;
  margin: 0 auto;
  margin-bottom: 10px;
  border: 3px solid greenyellow;
  padding: 10px 20px;
}
</style>
