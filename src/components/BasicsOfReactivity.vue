<script setup lang="ts">
import { reactive, ref } from 'vue'

const message = ref<string>('Инна')

interface TypeMaster {
  status: string
  experience: string
}
const master: TypeMaster = reactive({
  status: 'мастер',
  experience: 'высокий',
})

function changeName(): void {
  message.value = message.value === 'Инна' ? 'Магкеева Инна' : 'Инна'
}

function changeMasterInfo(): void {
  master.status = 'Мужской мастер'
  master.experience = 'более 20 лет'
}
</script>
<template>
  <div class="wrapper">
    <div>
      <h1>{{ message }}</h1>
      <button @click="changeName">показать полное имя</button>
    </div>
    <div>
      <h2>информация о мастере:</h2>
      <p>Статус: {{ master.status }}</p>
      <p>Стаж: {{ master.experience }}</p>
      <button @click="changeMasterInfo">уточнить информацию</button>
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
  margin-bottom: 3px;
}
</style>
