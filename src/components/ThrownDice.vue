<script setup>
// ThrownDice contains all logic for rolling + displaying dice
//note for myself -> diceArray contains face result
const diceArray = defineModel({ type: Array});

function diceThrow() {
    //reset dice
    const newDice = [];

    //roll dice 5 times
    for (let i = 0; i < 5; i++) {
        newDice.push(Math.floor(Math.random() * 6) + 1);
    } 
    diceArray.value = newDice;
}

//displays 5 rolled dice
function displayDice() {

}
</script>

<template>
<button @click="diceThrow">Throw!</button>



</template>