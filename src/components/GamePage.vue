<script setup lang="ts">
import { ref } from 'vue'
import ChipSwitch from './ChipSwitch.vue'
import Instructions from './Instructions.vue'

const score = ref(0)
const selectedNumber = ref<number | null>(null)
const rolledNumber = ref(1)
const showInstructions = ref(false)

const switchChoice = ref<string | null>(null)


function randomSwitchGuess() {
  const switchRandom = Math.floor(Math.random() * 2)
  switchChoice.value = switchRandom === 0 ? 'higher' : 'lower'
}

const resetScore = () => {
  score.value = 0
}

function selectNumber(num: number) {
  selectedNumber.value = selectedNumber.value === num ? null : num
}

function toggleInstructions() {
  showInstructions.value = !showInstructions.value
}

function rollDice() {
  if (selectedNumber.value === null) {
    alert('Please select a number before rolling the dice.')
    return
  }

  let result = Math.floor(Math.random() * 6) + 1
  while (result === rolledNumber.value) {
    result = Math.floor(Math.random() * 6) + 1
  }
  rolledNumber.value = result

  randomSwitchGuess()

  if (result === selectedNumber.value) {
    score.value += selectedNumber.value
  } else if (
    switchChoice.value === 'higher' && selectedNumber.value > rolledNumber.value
  ) {
    score.value += 1
  } else if (
    switchChoice.value === 'lower' && selectedNumber.value < rolledNumber.value
  ) {
    score.value += 1
  } else {
    score.value -= rolledNumber.value
  }
}
</script>

<template>
  <div class="main">
    <div class="contain">
      <div class="score">
        <h1>{{ score }}</h1>
        <h2>Total Score</h2>
      </div>

      <div class="box">
        <div
          v-for="num in 6"
          :key="num"
          :class="['innerbox', selectedNumber === num ? 'selected-box' : '']"
          @click="selectNumber(num)"
        >
          {{ num }}
        </div>
      </div>
    </div>

    <ChipSwitch  v-model="switchChoice" />

    <div class="dice" @click="rollDice">
      <h1>{{ rolledNumber }}</h1>
    </div>

    <div class="controller">
      <button @click="resetScore">Reset Score</button>
      <button class="instructions" @click="toggleInstructions">How to Play</button>
    </div>

    <Instructions v-if="showInstructions" />
  </div>
</template>

<style scoped>
.main {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 16px 24px;
  max-width: 1200px;
  margin: 0 auto;
  width: 100%;
}

.contain {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  width: 100%;
  padding: 16px;
  gap: 20px;
}

.score h1 {
  font-size: 96px;
  margin: 0;
}

.score h2 {
  font-size: 30px;
  font-weight: 500;
  margin-top: 8px;
}

.box {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  justify-content: center;
}

.innerbox {
  height: 72px;
  width: 72px;
  border: 1px solid black;
  display: grid;
  place-items: center;
  border-radius: 10px;
  font-size: 24px;
  font-weight: 700;
  cursor: pointer;
  transition: background-color 0.3s ease;
  background-color: white;
  color: black;
}

.innerbox:hover,
.innerbox.selected-box {
  background-color: black;
  color: white;
  border-color: white;
}

.dice {
  background-color: black;
  width: 300px;
  height: 300px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  border-radius: 12px;
  margin: 24px 0;
  font-size: 120px;
  user-select: none;
  cursor: pointer;
}

.controller {
  display: flex;
  flex-direction: column;
  gap: 16px;
  width: 300px;
  align-items: center;
}

button {
  background-color: black;
  padding: 10px 18px;
  color: white;
  border-radius: 5px;
  min-width: 220px;
  border: none;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: white;
  border: 1px solid black;
  color: black;
}

button.instructions {
  background-color: white;
  color: black;
  border: 1px solid black;
}

button.instructions:hover {
  background-color: black;
  color: white;
  border: none;
}

/* Responsive Styles */
@media (max-width: 768px) {



.box{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
}

 .score h1 {
    font-size: 64px;
  }

  .score h2 {
    font-size: 24px;
  }


}

@media (max-width: 400px) {
  .score h1 {
    font-size: 48px;
  }

  .score h2 {
    font-size: 20px;
  }

  .dice {
    width: 160px;
    height: 160px;
    font-size: 60px;
  }

  button {
    min-width: 180px;
    font-size: 14px;
  }

  .innerbox{
    font-size: 24px;
    width: 50px;
    height: 50px;
  }
}


</style>
