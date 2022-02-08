<script setup lang="ts">
import BoardRow from './BoardRow.vue'
import {ref} from 'vue'
import { Ref } from 'vue';

const board:Ref<string[]> = ref(Array(9).fill(null))
const nowPlayer = ref(true)
const winner = ref('')
const count = ref(0)
const handleClick = (i:number) => {
    const nowPlayerString = nowPlayer.value ? "○":"x"
    board.value.splice(i,1,nowPlayerString);
    checkAnswerVal()
    nowPlayer.value = !nowPlayer.value
    console.log(nowPlayer.value)
}
const checkAnswerVal = () => {
    const lines = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6],
    ];
  for (let i = 0; i < lines.length; i++) {
    const [a, b, c] = lines[i];
    if (board.value[a] && board.value[a] === board.value[b] && board.value[a] === board.value[c]) {
      winner.value = nowPlayer.value ? "○":"x"
    }
  }
}
</script>

<template>
    <div v-for="(item, index) in [[0,3],[3,6],[6,9]]" :key="index">
        <BoardRow v-for="(content,index2) in board.slice(item[0],item[1])" :rowContents="content" :i="index2+3*index" :onClick='handleClick' :key="content"/>
    </div>
    winner: {{winner}}
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
