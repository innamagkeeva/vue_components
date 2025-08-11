<script setup lang="ts">
import { ref } from 'vue'
import DisplayLetters from '@/components/DisplayLetters.vue'
const letters: string[] = [
  'A',
  'B',
  'C',
  'D',
  'E',
  'F',
  'G',
  'H',
  'I',
  'J',
  'K',
  'L',
  'M',
  'N',
  'O',
  'P',
  'Q',
  'R',
  'S',
  'T',
  'U',
  'V',
  'W',
  'X',
  'Y',
  'Z',
]
const symbols: string[] = [' ', '.', ',', '!', '?']

const outputText = ref('')

const warningMessage = ref('')
function addCharacter(char: string): void {
  const lastChar = outputText.value.slice(-1)
  if (lastChar === '.' && symbols.includes(char)) {
    warningMessage.value = `Нельзя ставить "${char}" после точки`
    return
  }
  warningMessage.value = ''
  outputText.value += char
}

function deleteCharacter(): void {
  outputText.value = outputText.value.slice(0, -1)
}
</script>
<template>
  <div class="wrapper">
    <div class="wrapper__inside">
      <DisplayLetters
        v-for="letter in letters"
        :key="letter"
        :char="letter"
        @addingLetter="addCharacter"
      />

      <button
        v-for="symbol in symbols"
        :key="symbol"
        :class="symbol === ' ' ? 'button_space' : 'button'"
        @click="addCharacter(symbol)"
      >
        {{ symbol }}
      </button>
      <button
        class="button button_delete"
        @click="deleteCharacter"
      >
        Удалить
      </button>
    </div>
    <div class="wrap">
      <div class="output">
        {{ outputText }}
      </div>
      <div
        v-if="warningMessage"
        class="warning"
      >
        {{ warningMessage }}
      </div>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-wrap: wrap;
  width: 500px;
  height: 700px;
  border: 2px solid green;
  margin: 0 auto;
  padding: 10px 20px;
  margin-bottom: 3px;
}

.wrapper__inside {
  height: 500px;
}

button {
  margin: 10px;
  background-color: green;
  height: 60px;
  width: 50px;
  border: none;
  border-radius: 20px;
  color: white;
  font-size: 20px;
  cursor: pointer;
}

.button_space {
  height: 30px;
}

.button_delete {
  width: 100px;
}

.button_delete:hover {
  background-color: darkred;
}

.wrap {
  position: relative;
  padding-bottom: 30px;
}

.output,
.warning {
  width: 400px;
  height: 40px;
  margin: 0 auto;

  font-size: 24px;
  border: 2px solid green;
  padding: 10px;
}

.warning {
  color: red;
  border: 1px solid red;
  font-size: 18px;
  position: absolute;
  bottom: 20px;
}
</style>
