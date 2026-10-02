<script setup>
import { ref } from 'vue'

import ScoreTable from './components/ScoreTable.vue';
import ThrownDice from './components/ThrownDice.vue';

//app.vue manages dice array + keep track of current rolled state
let count = { 0: 0, 1: 0, 2: 0, 3: 0, 4: 0, 5: 0 };

//v-model to link app.vue to ThrownDice
const diceArray = ref('count')
</script>

<template>

<ThrownDice v-model="diceArray"/>
<ScoreTable></ScoreTable>
</template>
