<script setup lang="ts">
import { ref } from 'vue'

const message = ref<string>('')
</script>
<template>
  <h1
    class="title"
    style="font-size: 40px"
  >
    Работа с формами.
  </h1>
  <div class="circuit">
    <p
      class="title"
      style="font-size: 25px"
    >
      Обычное использование
    </p>
    <input
      style="margin-bottom: 20px"
      v-model="message"
      type="text"
      placeholder="напечатай что-то"
    />
    <p class="textOutput">{{ message }}</p>
  </div>
</template>

<style scoped>
.title {
  text-align: center;
  color: crimson;
  font-size: 20px;
  margin-bottom: 20px;
}

.circuit {
  width: 500px;
  height: 910px;
  margin: 0 auto;
  margin-bottom: 10px;
  border: 2px solid cornflowerblue;
  padding: 20px;
}

.textOutput {
  width: 177px;
  height: 24px;
  border: 1px solid cornflowerblue;
  border-radius: 10px;
  padding: 0 10px;
}
</style>
