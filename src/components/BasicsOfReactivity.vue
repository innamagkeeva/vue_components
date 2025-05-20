<script setup lang="ts">
import { reactive, ref } from 'vue'

const message = ref('Инна!')

interface TypeMaster {
  name: string
  age: number
  experience: number
}
const master: TypeMaster = reactive({
  name: 'Инна',
  age: 35,
  experience: 3,
})

function changeName(): void {
  message.value = 'Инн!'
}

function changeMasterInfo(): void {
  master.name = 'Инн'
  master.age = 46
  master.experience = 20
}
</script>
<template>
  <div class="wrapper">
    <div>
      <h1>{{ message }}</h1>
      <button @click="changeName">изменить имя</button>
    </div>
    <div>
      <h2>информация о мастере:</h2>
      <p>Имя: {{ master.name }}</p>
      <p>Возраст: {{ master.age }}</p>
      <p>Стаж: {{ master.experience }}</p>
      <button @click="changeMasterInfo">изменить информацию</button>
    </div>
  </div>
</template>
<style scoped>
.wrapper {
  width: 500px;
  height: 300px;
  border: 1px solid green;
  margin: 0 auto;
  padding: 10px 20px;
}
</style>
