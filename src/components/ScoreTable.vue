<script setup>
import { computed } from 'vue'

const diceArray = defineModel({ type: Array, default: () => [] })

// counts[0] = number of ones ... counts[5] = number of sixes
const counts = computed(function () {
  const result = []

  for (let face = 1; face <= 6; face++) {
    let howMany = 0

    for (let i = 0; i < diceArray.value.length; i++) {
      const die = diceArray.value[i]
      if (die === face) {
        howMany = howMany + 1
      }
    }

    result.push(howMany)
  }

  return result
})

// sum of all dice
const sum = computed(function () {
  let total = 0

  for (let i = 0; i < diceArray.value.length; i++) {
    total = total + diceArray.value[i]
  }

  return total
})

// the highest count of any single face (e.g. three 4s -> 3)
const maxCount = computed(function () {
  let highest = 0

  for (let i = 0; i < counts.value.length; i++) {
    if (counts.value[i] > highest) {
      highest = counts.value[i]
    }
  }

  return highest
})

// "110111" means faces 1, 2, 4, 5, 6 are present -> straights are runs of 1s
const faces = computed(function () {
  let text = ''

  for (let i = 0; i < counts.value.length; i++) {
    if (counts.value[i] > 0) {
      text = text + '1'
    } else {
      text = text + '0'
    }
  }

  return text
})

// Part 1 scores: count of each face multiplied by the face value
const upper = computed(function () {
  const result = []

  for (let i = 0; i < counts.value.length; i++) {
    const faceValue = i + 1 // index 0 is face 1, index 1 is face 2, ...
    result.push(counts.value[i] * faceValue)
  }

  return result
})

const upperTotal = computed(function () {
  let total = 0

  for (let i = 0; i < upper.value.length; i++) {
    total = total + upper.value[i]
  }

  return total
})

// Part 2 scores
const lower = computed(function () {
  // Three of a Kind
  let threeOfAKind = 0
  if (maxCount.value >= 3) {
    threeOfAKind = sum.value
  }

  // Four of a Kind
  let fourOfAKind = 0
  if (maxCount.value >= 4) {
    fourOfAKind = sum.value
  }

  // Full House: one face appears 3 times AND another appears 2 times
  let fullHouse = 0
  if (counts.value.includes(3) && counts.value.includes(2)) {
    fullHouse = 25
  }

  // Small Straight: four faces in a row, e.g. "1111" inside "011110"
  let smallStraight = 0
  if (faces.value.includes('1111')) {
    smallStraight = 30
  }

  // Large Straight: five faces in a row
  let largeStraight = 0
  if (faces.value.includes('11111')) {
    largeStraight = 40
  }

  // Yahtzee: all five dice show the same face
  let yahtzee = 0
  if (maxCount.value === 5) {
    yahtzee = 50
  }

  return {
    'Three of a Kind': threeOfAKind,
    'Four of a Kind': fourOfAKind,
    'Full House': fullHouse,
    'Small Straight': smallStraight,
    'Large Straight': largeStraight,
    'Yahtzee': yahtzee,
    'Chance': sum.value,
  }
})
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

    <tr>
        <th>Three of a Kind</th>
        <td>{{ threeOfAKind }}</td></tr>
    <tr>
        <th>Four of a Kind</th>
        <td>{{ fourOfAKind }}</td></tr>
    <tr>
        <th>Full House</th>
        <td>{{ fullHouse }}</td></tr>
    <tr>
        <th>Small Straight</th>
        <td>{{ smallStraight }}</td></tr>
    <tr>
        <th>Large Straight</th>
        <td>{{ largeStraight }}</td></tr>
    <tr>
        <th>Yahtzee</th>
        <td>{{ yahtzee }}</td></tr>
    <tr>
        <th>Chance</th>
        <td>{{ chance }}</td></tr>
  </table>
</template>