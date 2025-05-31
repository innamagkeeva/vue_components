<script setup lang="ts">
import { ref } from 'vue'

const workingDay = ref<boolean>(false)

const type = ref('') //Это же не нужно типизировать? потому что мы сами ничего не вводим, а только выбираем из возможных вариантов?
</script>
<template>
  <h1 class="title">Условная отрисовка</h1>
  <div class="circuit">
    <p
      class="title"
      style="font-size: 30px"
    >
      v-if / v-else
    </p>
    <div class="cloth">
      <div v-if="workingDay">сегодня рабочий день</div>
      <div v-else>сегодня выходной день</div>
    </div>
  </div>
  <div
    class="circuit"
    style="height: 285px"
  >
    <p
      class="title"
      style="font-size: 30px"
    >
      v-else-if
    </p>
    <div class="selectClass">
      <select
        v-model="type"
        class="selectStyle"
      >
        <option value="">Выберете тип</option>
        <option value="A">тип А</option>
        <option value="B">тип B</option>
        <option value="C">тип C</option>
      </select>
    </div>

    <div
      class="typeValue"
      v-if="type === 'A'"
    >
      Вы выбрали тип A
    </div>
    <div
      class="typeValue"
      v-else-if="type === 'B'"
    >
      Вы выбрали тип B
    </div>
    <div
      class="typeValue"
      v-else-if="type === 'C'"
    >
      Вы выбрали тип C
    </div>
    <div
      class="typeValue"
      v-else
    >
      Не выбран тип
    </div>
  </div>
</template>
<style>
.cloth {
  width: 400px;
  height: 20px;
  font-size: 19px;
  border: 3px solid hotpink;
  margin: 0 auto;
  padding: 10px 20px;
  margin-bottom: 10px;
}

.title {
  text-align: center;
  color: darkblue;
  font-size: 40px;
}

.selectClass {
  margin: 0 auto;
  text-align: center;
  border: 3px solid hotpink;
  width: 400px;
  height: 70px;
  padding-top: 10px;
  margin-bottom: 20px;
}

.selectStyle {
  width: 200px;
  height: 50px;
  border: 1px solid black;
}

.typeValue {
  margin: 0 auto;
  text-align: center;
  border: 1px solid yellowgreen;
  width: 200px;
  height: 50px;
  padding-top: 20px;
}

.circuit {
  width: 500px;
  height: 170px;
  border: 2px solid green;
  margin: 0 auto;
  margin-bottom: 10px;
}
</style>
