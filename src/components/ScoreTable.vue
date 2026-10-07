<script setup>
import { computed } from 'vue'

const numberToWord = (num) => {
  const words = [
    'One',
    'Two',
    'Three',
    'Four',
    'Five',
    'Six',
  ]
  return words[num] ?? num
}

const diceArray = defineModel()

// finds
// counts[0] = number of 1s
const counts = computed(() =>
  [1, 2, 3, 4, 5, 6].map(n => diceArray.value.filter(d => d === n).length)
)

const sum = computed(() => diceArray.value.reduce((a, b) => a + b, 0))
const maxCount = computed(() => Math.max(...counts.value))

// "110111" means faces 1, 2, 4, 5, 6 are present -> straights are runs of 1s
const faces = computed(() => counts.value.map(c => (c > 0 ? 1 : 0)).join(''))

const upper = computed(() => counts.value.map((c, i) => c * (i + 1)))
const upperTotal = computed(() => upper.value.reduce((a, b) => a + b, 0))

// distinguish between 3/4 of a kind and change
const lower = computed(() => ({
  'Three of a Kind': maxCount.value >= 3 ? sum.value : 0,
  'Four of a Kind': maxCount.value >= 4 ? sum.value : 0,
  'Full House': counts.value.includes(3) && counts.value.includes(2) ? 25 : 0,
  'Small Straight': faces.value.includes('1111') ? 30 : 0,
  'Large Straight': faces.value.includes('11111') ? 40 : 0,
  'Yahtzee': maxCount.value === 5 ? 50 : 0,
  'Change': sum.value,
}))
</script>

<template>
  <table class="table">
    <tr>
      <th>Part 1</th>
      <th>Score</th>
    </tr>

    <tr v-for="(score, index) in upper" :key="index">
      <th>{{ numberToWord(index) }}</th>
      <td>{{ score }}</td>
    </tr>

    <tr>
      <th>Total Points</th>
      <td>{{ upperTotal }}</td>
    </tr>

    <tr>
      <th>Part 2</th>
      <th></th>
    </tr>

    <tr v-for="(score, name) in lower" :key="name">
        <th>{{ name }}</th>
        <td>{{ score }}</td>
    </tr>
    
  </table>
</template>