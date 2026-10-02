<script setup>
import { ref } from 'vue'

import ScoreTable from './components/ScoreTable.vue';
import ThrownDice from './components/ThrownDice.vue';

//app.vue manages dice array + keep track of current rolled state
const dice = ref([])

//v-model to link app.vue to ThrownDice
const diceArray = ref('count')
</script>

<template>

<ThrownDice v-model="diceArray"/>
<ScoreTable></ScoreTable>
</template>
