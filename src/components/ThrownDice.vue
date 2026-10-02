<script setup>
// ThrownDice contains all logic for rolling + displaying dice
import { ref } from 'vue'

//note for myself -> diceArray contains face result
const diceArray = defineModel({type: Array});

function diceThrow() {
    //reset dice
    diceArray.value = []

    //roll dice 5 times
    for (let i = 0; i < 5; i++) {
        const roll = Math.floor(Math.random() * 6) + 1;
        diceArray.value.push(roll);
    } 
}

//displays 5 rolled dice

</script>

<template>
<button @click="diceThrow">Throw!</button>

<div v-for="(dice, index) in diceArray" :key="index">
    {{ dice }}
</div>

</template>