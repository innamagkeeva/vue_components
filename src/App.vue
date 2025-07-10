<script setup lang="ts">
import TemplateSyntax from '@/components/TemplateSyntax.vue'
import BasicsOfReactivity from '@/components/BasicsOfReactivity.vue'
import ComputedProperties from '@/components/ComputedProperties.vue'
import ClassesAndStyles from '@/components/ClassesAndStyles.vue'
import ConditionalRendering from '@/components/ConditionalRendering.vue'
import RenderingLists from '@/components/RenderingLists.vue'
import EventHandling from '@/components/EventHandling.vue'
import WorkingWithForms from '@/components/WorkingWithForms.vue'
import KeyboardButtons from '@/components/KeyboardButtons.vue'
</script>

<template>
  <div>
    <TemplateSyntax />
    <BasicsOfReactivity />
    <ComputedProperties />
    <ClassesAndStyles />
    <ConditionalRendering />
    <RenderingLists />
    <EventHandling />
    <WorkingWithForms />
    <KeyboardButtons />
  </div>
</template>
<style>
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}

body,
h1,
h2,
p,
ul,
li {
  margin: 0;
}

ul {
  list-style: none;
  padding: 0;
}
</style>
