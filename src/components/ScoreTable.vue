<script setup>
// displays table with all yahtzee scores

//v-model to pass dice array from Vue to ScoreTable
const diceArray = defineModel();

</script>

<template>

    <table>
        <tr>
            <th> Part 1 </th>
            <th> Score </th>
        </tr>

        <tr>
            <th> 1 through 6 temp </th>
            <th> score temp </th>
        </tr>

        <tr>
            <th> Total Points </th>
            <th> </th>
        </tr>

        <tr>
            <th>Part 2</th>
            <th> </th>
        </tr>

         <tr>
            <th>Three of a Kind</th>
            <td></td>
        </tr>
        
        <tr>
            <th>Four of a Kind</th>
            <td></td>
        </tr>
        
        <tr>
            <th>Full House</th>
            <td></td>
        </tr>
        
        <tr>
            <th>Small Straight</th>
            <td></td>
        </tr>
        
        <tr>
            <th>Large Straight</th>
            <td></td>
        </tr>

        <tr>
            <th>Yahtzee</th>
            <td></td>
        </tr>
        
        <tr>
            <th>Change</th>
            <td></td>
        </tr>

    </table>
</template>
