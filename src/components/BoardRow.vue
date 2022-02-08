<script setup lang="ts">
import Square from './Square.vue'
type type = (i:number) => void
defineProps<{rowContents:string|undefined,onClick:type, i:number}>()

</script>

<template>
    <Square :count="rowContents" :i="i" :onClick="onClick"/>
</template>

<style scoped>
/* a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
} */
</style>
