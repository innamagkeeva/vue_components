<script setup lang="ts">
import TemplateSyntax from '@/components/TemplateSyntax.vue'
import BasicsOfReactivity from '@/components/BasicsOfReactivity.vue'
import ComputedProperties from '@/components/ComputedProperties.vue'
import ClassesAndStyles from '@/components/ClassesAndStyles.vue'
</script>

<template>
  <div class="wrapper">
    <TemplateSyntax></TemplateSyntax>
    <BasicsOfReactivity></BasicsOfReactivity>
    <ComputedProperties></ComputedProperties>
  </div>
  <div class="wrapper">
    <ClassesAndStyles></ClassesAndStyles>
  </div>
  <div></div>
</template>
<style>
.wrapper {
  max-width: 100%;
  height: 100vh;
  border: 1px solid darkmagenta;
  padding: 20px;
  margin-bottom: 5px;
}
</style>
