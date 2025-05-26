<script setup lang="ts">
import { reactive, ref, computed } from 'vue'

type BasActiveClothing = true | false
type BasHasError = boolean

interface ErrorType {
  type: string
}

interface BasClassObject {
  cloth: boolean
  activeClothing: boolean
  'text-danger': boolean
}

const isActiveClothing = ref<BasActiveClothing>(true)
const error = ref<ErrorType | null>(null)
const hasError = ref<BasHasError>(false)
const clothClass = ref('cloth')
const activeClothingClass = ref('activeClothing')
const errorClass = ref('text-danger')

const classObject: BasClassObject = reactive({
  cloth: true,
  activeClothing: true,
  'text-danger': Boolean(hasError.value),
})

const objectClass = computed<BasClassObject>(() => ({
  cloth: true,
  activeClothing: isActiveClothing.value,
  'text-danger': error.value?.type === 'fatal',
}))
</script>

<template>
  <div
    class="cloth"
    :class="{ activeClothing: isActiveClothing }"
  >
    Активный элемент
  </div>
  <div :class="classObject">Объектный синтаксис</div>
  <div :class="objectClass">Вычисляемые свойства</div>
  <div :class="[clothClass, activeClothingClass, errorClass]">Синтаксис с массивом</div>
  <div
    :class="[clothClass, isActiveClothing ? activeClothingClass : '', hasError ? errorClass : '']"
  >
    Тернарный оператор в массиве
  </div>
</template>
<style scoped>
.cloth {
  width: 500px;
  height: 20px;
  border: 3px solid hotpink;
  margin: 0 auto;
  padding: 10px 20px;
  margin-bottom: 10px;
}

.activeClothing {
  background-color: indianred;
  color: white;
}

.text-danger {
  color: red;
}
</style>
