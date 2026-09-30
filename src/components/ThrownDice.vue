<script setup>
//roll 5 dice

function diceThrow() {
    //reset dice
    count = { 0: 0, 1: 0, 2: 0, 3: 0, 4: 0, 5: 0 };

    //roll dice 5 times
    for (let i = 0; i < 5; i++) {
        const roll = Math.floor(Math.random() * 6) + 1;
        count[roll - 1] = count[roll - 1] + 1;
    } 
}
//displays 5 rolled dice

</script>

<template>


<button @click="diceThrow">Throw!</button>
    
</template>