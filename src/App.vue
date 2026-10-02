<script setup>
import { ref } from 'vue'

import ScoreTable from './components/ScoreTable.vue';
import ThrownDice from './components/ThrownDice.vue';

//app.vue manages dice array + keep track of current rolled state
const dice = ref([])

//const diceArray = ref('')
</script>

<template>

<ThrownDice v-model="dice"/>
<ScoreTable v-model="dice"/>
</template>
