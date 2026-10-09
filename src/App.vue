<script setup>
import { ref } from 'vue'

import ScoreTable from './components/ScoreTable.vue';
import ThrownDice from './components/ThrownDice.vue';

// dice array, keeps track of current rolled state
const dice = ref([1,2,3,4,5,6])
</script>

<template>
    <h3>---Yahtzee---</h3>

<ThrownDice v-model="dice"/>
<ScoreTable v-model="dice"/>
</template>
