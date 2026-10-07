<script setup>
import { ref } from 'vue'

import ScoreTable from './components/ScoreTable.vue';
import ThrownDice from './components/ThrownDice.vue';

// dice array, keeps track of current rolled state
const dice = ref([])

</script>

<template>
    <h3>---Yahtzee---</h3>

    <ThrownDice v-model="dice"/>
    <ScoreTable v-model="dice"/>
</template>
