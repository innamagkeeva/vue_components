<script setup lang="ts">
const props = defineProps<{
  char: string
}>()

const imit = defineEmits<{
  (e: 'addendum', value: string): void
}>()

function onClick() {
  imit('addendum', props.char)
}
</script>
<template>
  <button @click="onClick">
    {{ char }}
  </button>
</template>
<style scoped>
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
</style>
