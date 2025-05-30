<script setup lang="ts">
import { reactive, ref, computed } from 'vue'

interface ErrorType {
  type: string
}

interface BasClassObject {
  cloth: boolean
  activeClothing: boolean
  'text-danger': boolean
}
interface BasStyleObject {
  color: string
  fontSize: string
  height: string
}

const isActiveClothing = ref<boolean>(true)
const error = ref<ErrorType | null>(null)
const hasError = ref<boolean>(false)
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

const activeColor = ref<string>('orange')
const fontSize = ref<number>(30)
const height = ref<number>(43)

//ВОПРОС: почему в стилях тип вставляется в reactive, а в классах в сонстанту? Это я определила методом тыка, потому что как в классе - выдавало ошибку.
const styleObject = reactive<BasStyleObject>({
  color: 'blue',
  fontSize: '22px',
  height: '31px',
})

const colorComputed = ref<string>('saddlebrown')
const fontSizeComputed = ref<string>('24px')
const heightComputed = ref<string>('37px')
const backgroundColorComputed = ref<string>('slategray')

const computedStyle = computed(() => ({
  color: colorComputed.value,
  fontSize: fontSizeComputed.value,
  height: heightComputed.value,
  backgroundColor: backgroundColorComputed.value,
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
  <div
    class="cloth"
    :style="{ color: activeColor, fontSize: fontSize + 'px', height: height + 'px' }"
  >
    Инлайн-стили
  </div>
  <div
    class="cloth"
    :style="styleObject"
  >
    Инлайн-стили.Объектный синтаксис
  </div>
  <div
    class="cloth margin-bottom"
    :style="computedStyle"
  >
    Инлайн-стили. Вычисляемые свойства
  </div>
</template>
<style scoped>
.cloth {
  width: 500px;
  height: 20px;
  font-size: 17px;
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

.margin-bottom {
  margin-bottom: 20px;
}
</style>
