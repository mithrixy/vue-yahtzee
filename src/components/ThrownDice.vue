<script setup>
// ThrownDice contains all logic for rolling + displaying dice
//roll 5 dice


function diceThrow() {
    //reset dice

    //roll dice 5 times
    for (let i = 0; i < 5; i++) {
        const roll = Math.floor(Math.random() * 6) + 1;
        count[roll - 1] = count[roll - 1] + 1;
    } 
}

//displays 5 rolled dice


//v-model to pass dice array from Vue to Throw
const diceArray = defineModel();
</script>

<template>
<button @click="diceThrow">Throw!</button>

</template>