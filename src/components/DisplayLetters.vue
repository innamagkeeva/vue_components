<script setup lang="ts">
const props = defineProps<{
  char: string
}>()

const imit = defineEmits<{
  addingLetter: [value: string]
}>()

function onClick() {
  imit('addingLetter', props.char)
}
</script>

<template>
  <button @click="onClick">
    {{ char }}
  </button>
</template>
