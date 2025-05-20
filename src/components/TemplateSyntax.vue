<script setup lang="ts">
import { ref } from 'vue'
const greetings = ref('Привет!!')

function addSign(): void {
  greetings.value += '!'
}

function deleteSign(): void {
  greetings.value = greetings.value.slice(0, -1)
}
</script>

<template>
  <div class="wrapper">
    <h1 class="greetings">{{ greetings }}</h1>
    <button
      class="btnSign"
      @click="addSign"
    >
      добавить !
    </button>
    <button
      class="btnSign"
      @click="deleteSign"
      v-if="greetings.length > 8"
    >
      Удалить !
    </button>
  </div>
</template>

<style scoped>
.wrapper {
  width: 500px;
  height: 120px;
  border: 1px solid red;
  margin: 0 auto;
  margin-bottom: 5px;
  padding: 10px 20px;
}

.greetings {
  color: red;
}
</style>
