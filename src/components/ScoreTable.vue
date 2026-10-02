<script setup>
import { computed } from 'vue'

const diceArray = defineModel({ type: Array, default: () => [] })

 


</script>

<template>
  <table>
    <tr>
      <th>Part 1</th>
      <th>Score</th>
    </tr>

    <tr v-for="(score, index) in upperScores" :key="index">
      <th>{{ index + 1 }}</th>
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