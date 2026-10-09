<script setup>
// ThrownDice contains all logic for rolling + displaying dice
//note for myself -> diceArray contains face result
const diceArray = defineModel();

function diceThrow() {
    //reset dice
    const newDice = [];

    //roll dice 5 times
    for (let i = 0; i < 5; i++) {
        newDice.push(Math.floor(Math.random() * 6) + 1);
    } 
    diceArray.value = newDice;
}
</script>

<template>

    <div>
        <img v-for="(image, index) in dice"
            :key="index"
            :src="/src/assets/dice${die}.png"
      />
    </div>
    

    <button @click="diceThrow">Throw!</button>

</template>