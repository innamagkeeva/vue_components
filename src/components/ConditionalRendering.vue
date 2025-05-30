<script setup lang="ts">
import { ref } from 'vue'

const workingDay = ref<boolean>(false)
</script>
<template>
  <h1 class="centered">Условная отрисовка</h1>
  <div>
    <div
      class="cloth"
      v-if="workingDay"
    >
      сегодня рабочий день
    </div>
    <div
      class="cloth"
      v-else
    >
      сегодня выходной день
    </div>
  </div>
</template>
<style>
.cloth {
  width: 500px;
  height: 20px;
  font-size: 17px;
  border: 3px solid hotpink;
  margin: 0 auto;
  padding: 10px 20px;
  margin-bottom: 10px;
}

.centered {
  text-align: center;
  color: darkblue;
}
</style>
