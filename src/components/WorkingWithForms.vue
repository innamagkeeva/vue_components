<script setup lang="ts">
import { computed, ref } from 'vue'
type BasChecked = true | false
type BasCheckedNames = 'Jack' | 'John' | 'Mike' | 'Duduk'
type BasSelectedColor = 'Красный' | 'Синий' | 'Зеленый' | 'цвет не выбран'
type BasTypeSelect = '1' | '2' | '3' | '4'
interface Option {
  value: string
  text: string
}
type BasSelectType = 'A' | 'B' | 'C' | 'D' | ''
type BasPick = 'Первый' | 'Второй' | null

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

const selectedColor = ref<BasSelectedColor>('цвет не выбран')

const selectType = ref<BasSelectType>('')
const typeSelect = ref<BasTypeSelect[]>([])

const selected = ref<string>('A')
const options = ref<Option[]>([
  { text: 'один', value: 'A' },
  { text: 'два', value: 'B' },
  { text: 'три', value: 'C' },
])

const toggle = ref<string>('да')

const choose = ref<string | null>(null)
const dynamicTrueValue = ref<string>('статус: Да')
const dynamicFalseValue = ref<string>('статус: уже нет')

const pick = ref<BasPick>(null)

const marked = ref<string>('')
</script>

<template>
  <h1
    class="title"
    style="font-size: 40px"
  >
    Работа с формами.
  </h1>
  <div class="circuit">
    <p class="title">Обычное использование. Текст</p>
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
      style="cursor: pointer"
      type="checkbox"
      id="Mike"
      value="Mike"
      v-model="checkedNames"
    />
    <label for="Mike">Mike</label>

    <label class="checkbox-item">
      <input
        type="checkbox"
        value="Duduk"
        v-model="checkedNames"
      />
      Duduk
    </label>
    <p class="title">Радиокнопки</p>
    <p
      class="title"
      style="font-size: 16px"
    >
      Выберите цвет
    </p>

    <input
      type="radio"
      id="red"
      name="color"
      value="Красный"
      v-model="selectedColor"
      class="radio-item"
    />
    <label
      for="red"
      class="radio-label"
      style="color: red"
      >красный</label
    >
    <input
      type="radio"
      id="blue"
      name="color"
      value="Синий"
      v-model="selectedColor"
      class="radio-item"
    />
    <label
      for="blue"
      class="radio-label"
      style="color: blue"
      >Синий</label
    >
    <input
      type="radio"
      id="green"
      name="color"
      v-model="selectedColor"
      value="Зеленый"
      class="radio-item"
    />
    <label
      for="green"
      class="radio-label"
      style="color: green"
      >Зеленый</label
    >
    <div style="margin-bottom: 20px">Выбран цвет: {{ selectedColor }}</div>
    <p class="title">Выпадающие списки</p>
    <p
      class="title"
      style="font-size: 16px"
    >
      Выбор одного варианта из списка:
    </p>
    <div class="selectPlace">
      <select
        class="SelectStyle"
        v-model="selectType"
      >
        <option
          disabled
          value=""
        >
          Выберите один из вариантов
        </option>
        <option value="A">вариант: A</option>
        <option value="B">вариант: B</option>
        <option value="C">вариант: C</option>
        <option value="D">вариант: D</option>
      </select>
    </div>
    <div class="selectedOption">Выбран вариант: {{ selectType || 'пока ничего не выбрано' }}</div>
    <p
      class="title"
      style="font-size: 16px"
    >
      Выбор нескольких вариантов из списка (с привязкой к массиву):
    </p>
    <p
      class="title"
      style="font-size: 13px"
    >
      Для выбора нескольких вариантов необходимо удерживать клавишу Ctrl
    </p>
    <div class="selectPlace">
      <select
        class="SelectStyle"
        style="height: 90px"
        v-model="typeSelect"
        multiple
      >
        <option value="1">Вариант: 1</option>
        <option value="2">Вариант: 2</option>
        <option value="3">Вариант: 3</option>
        <option value="4">Вариант: 4</option>
      </select>
    </div>
    <div class="selectedOption">Вы выбрали вариант(ы): {{ typeSelect.join(', ') }}</div>
    <p class="title">Динамическое отображение списка опций с помощью v-for:</p>
    <div class="selectPlace">
      <select
        class="SelectStyle"
        v-model="selected"
      >
        <option
          v-for="option in options"
          :key="option.value"
          :value="option.value"
        >
          {{ option.text }}
        </option>
      </select>
    </div>
    <div
      class="selectedOption"
      style="height: 40px"
    >
      Выбрано: {{ selected }}
    </div>
    <p class="title">Привязка значений</p>
    <p
      class="title"
      style="color: blueviolet"
    >
      Чекбокс
    </p>
    <div style="display: flex; font-size: 20px">
      <input
        class="checkbox-style"
        type="checkbox"
        v-model="toggle"
        true-value="да"
        false-value="нет"
      />
      <p>Значение: {{ toggle }}</p>
    </div>
    <div style="display: flex; font-size: 20px">
      <input
        class="checkbox-style"
        type="checkbox"
        :true-value="dynamicTrueValue"
        :false-value="dynamicFalseValue"
        v-model="choose"
      />
      <p>{{ choose }}</p>
    </div>
    <p
      class="title"
      style="color: blueviolet"
    >
      Радиокнопки
    </p>
    <div>
      <input
        class="radio-item"
        type="radio"
        v-model="pick"
        value="Первый"
      />
    </div>
    <div style="display: flex">
      <input
        class="radio-item"
        type="radio"
        v-model="pick"
        value="Второй"
      />
    </div>
    <p style="margin-bottom: 20px">Вы выбрали: {{ pick }}</p>
    <p
      class="title"
      style="color: blueviolet"
    >
      Выпадающие списки
    </p>
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
  height: 2200px;
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
  cursor: pointer;
}

.checkbox-item {
  display: block;
  margin-bottom: 10px;
  font-size: 16px;
  color: #333;
  cursor: pointer;
}

.radio-item {
  width: 20px;
  height: 20px;
  margin: 10px;

  cursor: pointer;
}

.radio-label {
  font-size: 20px;
  margin-right: 20px;
}

.selectPlace {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.SelectStyle {
  width: 300px;
  height: 50px;
  padding: 10px;
  margin: 0 auto;
}

.selectedOption {
  width: 230px;
  height: 60px;
  border: 1px solid black;
  margin: 0 auto;
  text-align: center;
  font-size: 16px;
  margin-bottom: 20px;
  padding: 10px;
}
</style>
