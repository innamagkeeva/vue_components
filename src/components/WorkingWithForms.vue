<script setup lang="ts">
import { computed, ref } from 'vue'
type BasChecked = true | false
type BasCheckedNames = 'Jack' | 'John' | 'Mike'

const message = ref<string>('')
const multilineMessage = ref<string>('')
const checked = ref<BasChecked>(true)

const checkedNames = ref<BasCheckedNames[]>([])
const checkedNamesText = computed(() => {
  if (checkedNames.value.length === 0) {
    return 'Никто не выбран'
  }
  return `${checkedNames.value.join(', ')}`
})
</script>
<template>
  <h1
    class="title"
    style="font-size: 40px"
  >
    Работа с формами.
  </h1>
  <div class="circuit">
    <p class="title">Обычное использование</p>
    <input
      class="window-style"
      style="height: 24px"
      v-model="message"
      type="text"
      placeholder="напечатай что-то"
    />
    <p class="text-output">{{ message }}</p>
    <p class="title">Многострочный текст</p>
    <textarea
      type="text"
      class="window-style"
      v-model="multilineMessage"
      placeholder="Введите несколько строк"
    >
    </textarea>
    <div
      class="text-output"
      style="white-space: pre-line; height: 70px; overflow-y: auto"
    >
      {{ multilineMessage }}
    </div>
    <p class="title">Чекбоксы</p>
    <input
      type="checkbox"
      id="checkbox"
      class="checkbox-style"
      v-model="checked"
    />
    <label
      for="checkbox"
      style="font-size: 30px"
      >{{ checked }}</label
    >
    <p class="title">Список чекбоксов, привязанных к массиву или значениям Set:</p>
    <div style="margin-bottom: 20px">Отмеченные имена: {{ checkedNamesText }}</div>
    <input
      type="checkbox"
      id="Jack"
      value="Jack"
      v-model="checkedNames"
    />
    <label
      for="Jack"
      style="margin-right: 20px"
      >Jack</label
    >
    <input
      type="checkbox"
      id="John"
      value="John"
      v-model="checkedNames"
    />
    <label
      for="John"
      style="margin-right: 20px"
      >John</label
    >
    <input
      type="checkbox"
      id="Mike"
      value="Mike"
      v-model="checkedNames"
    />
    <label for="Mike">Mike</label>
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

.text-output {
  width: 277px;
  height: 24px;
  border: 1px solid cornflowerblue;
  border-radius: 10px;
  padding: 0 10px;
  margin-bottom: 20px;
  cursor: pointer;
}

.window-style {
  width: 277px;
  height: 70px;
  margin-bottom: 20px;
  cursor: pointer;
}

.checkbox-style {
  width: 30px;
  height: 30px;
  margin: 0 20px 20px 0;
}
</style>
