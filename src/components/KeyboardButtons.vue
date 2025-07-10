<script setup lang="ts">
import { ref } from 'vue'

const result = ref('')
function getResult(str: string): void {
  result.value += str
}
function deleteSign(): void {
  result.value = result.value.slice(0, -1)
}
</script>

<template>
  <div class="wrapper">
    <div class="wrapper__inside">
      <button
        class="button"
        @click="getResult('A')"
      >
        A
      </button>
      <button
        class="button"
        @click="getResult('B')"
      >
        B
      </button>
      <button
        class="button"
        @click="getResult('C')"
      >
        C
      </button>
      <button
        class="button"
        @click="getResult('D')"
      >
        D
      </button>
      <button
        class="button"
        @click="getResult('F')"
      >
        F
      </button>
      <button
        class="button"
        @click="getResult('G')"
      >
        G
      </button>
      <button
        class="button"
        @click="getResult('H')"
      >
        H
      </button>
      <button
        class="button"
        @click="getResult('I')"
      >
        I
      </button>
      <button
        class="button"
        @click="getResult('J')"
      >
        J
      </button>
      <button
        class="button"
        @click="getResult('K')"
      >
        K
      </button>
      <button
        class="button"
        @click="getResult('L')"
      >
        L
      </button>
      <button
        class="button"
        @click="getResult('M')"
      >
        M
      </button>
      <button
        class="button"
        @click="getResult('N')"
      >
        N
      </button>
      <button
        class="button"
        @click="getResult('O')"
      >
        O
      </button>
      <button
        class="button"
        @click="getResult('P')"
      >
        P
      </button>
      <button
        class="button"
        @click="getResult('Q')"
      >
        Q
      </button>
      <button
        class="button"
        @click="getResult('R')"
      >
        R
      </button>
      <button
        class="button"
        @click="getResult('S')"
      >
        S
      </button>
      <button
        class="button"
        @click="getResult('T')"
      >
        T
      </button>
      <button
        class="button"
        @click="getResult('U')"
      >
        U
      </button>
      <button
        class="button"
        @click="getResult('V')"
      >
        V
      </button>
      <button
        class="button"
        @click="getResult('W')"
      >
        W
      </button>
      <button
        class="button"
        @click="getResult('X')"
      >
        X
      </button>
      <button
        class="button"
        @click="getResult('Y')"
      >
        Y
      </button>
      <button
        class="button"
        @click="getResult('Z')"
      >
        Z
      </button>
      <button
        class="button_space"
        @click="getResult(' ')"
      ></button>
      <button
        class="button"
        v-if="result.length > 0"
        @click="getResult('.')"
      >
        .
      </button>
      <button
        class="button"
        v-if="result.length > 0 && result.slice(-1) !== '.'"
        @click="getResult(',')"
      >
        ,
      </button>
      <button
        class="button"
        v-if="result.length > 0 && result.slice(-1) !== '.'"
        @click="getResult('!')"
      >
        !
      </button>
      <button
        class="button"
        v-if="result.length > 0 && result.slice(-1) !== '.'"
        @click="getResult('?')"
      >
        ?
      </button>
      <button
        class="button_delete"
        @click="deleteSign"
      >
        DELETE
      </button>
    </div>
    <h1 class="result">{{ result }}</h1>
  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;

  width: 500px;
  height: 600px;
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
</style>
