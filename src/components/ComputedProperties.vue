<script setup lang="ts">
import { computed, ref } from 'vue'

type MastersNames = 'Инна' | 'Татьяна' | 'Марина'

interface Master {
  name: MastersNames
  experience: number
}

const master = ref<Master>({
  name: 'Татьяна',
  experience: 10,
})
const experience = computed(() => {
  return master.value.experience > 7 ? 'Опытная' : 'Новичок'
})
</script>

<template>
  <div class="wrapper">
    <h1>Информация о мастере:</h1>
    <p>Имя: {{ master.name }}</p>
    <p>Опыт: {{ master.experience }} лет</p>
    <p>Статус: {{ experience }}</p>
  </div>
</template>

<style scoped>
.wrapper {
  width: 500px;
  height: 180px;
  border: 1px solid blue;
  margin: 0 auto;
  margin-bottom: 20px;
  padding: 10px 20px;
}
</style>
