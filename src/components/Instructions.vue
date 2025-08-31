

<!-- src/components/Instructions.vue -->
<template>
  <div id="instructions-box">
    <h3>How to Play</h3>
    <ul>
      <li>Select a number from 1 to 6.</li>
      <li>Click on Dice to roll.</li>
      <li>If the dice matches your selected number, you gain points equal to that number.</li>
      <li>If not, you lose that number of points.</li>
      <li>Additionally, if the random switch matches your number logic (higher/lower), you get +1 without any penalty.</li>
    </ul>
  </div>
</template>

<style scoped>
#instructions-box {
  border: 2px solid red;
  padding: 16px;
  margin-top: 20px;
  border-radius: 8px;
  background-color: #fff5f5;
  color: #333;
  font-size: 16px;
  max-width: 500px;
}
#instructions-box ul {
  padding-left: 20px;
  margin: 0;
}
</style>
