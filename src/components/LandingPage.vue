<script setup lang="ts">

import { defineEmits } from 'vue';

const emits = defineEmits(["onClick"]);
const handleClick = () => {
  emits('onClick')
}

</script>


<template>

    <div class="contain">
        <div class="object">
            <img src="/dices.png" alt="">
        </div>
        <div>
            <h1>Dice Game</h1>
            <div class="btn">
                <button @click="handleClick">Play Game</button>
            </div>
        </div>
    </div>
</template>


<style scoped>


h1{
    font-size: 96px;
    white-space: nowrap ;
    padding-bottom: 16px;
}

.btn{
    display: flex;
    justify-content: flex-end;
}
.object img {
  width: 100%;
  max-width: 50vw;
  min-width: 300px;
  height: auto;
  object-fit: contain;
}


.contain {
  max-width: 1190px;
  height: 100vh;
  display: flex;
  margin: 0 auto;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 16px;
  gap: 32px;
}



h1 {
  font-size: 72px;
  white-space: nowrap;
  padding-bottom: 16px;
}

.btn {
  display: flex;
  justify-content: flex-end;
  flex-wrap: wrap;
}

button {
  background-color: black;
  padding: 10px 18px;
  color: white;
  border-radius: 5px;
  min-width: 220px;
  border: none;
  font-size: 16px;
  border: 1px solid transparent;
  cursor: pointer;
  transition: 0.4s background-color ease-in;
}

button:hover {
  background-color: white;
  border: 1px solid black;
  color: black;
  transition: 0.3s background-color ease-in;
}

@media (max-width: 768px) {
  .contain {
    flex-direction: column;
    text-align: center;
    height: auto;
    padding-top: 40px;
  }

  h1 {
    font-size: 48px;
  }

  .btn {
    justify-content: center;
    margin-top: 20px;
  }

  .object img {
    width: 200px;
  }
}

@media (max-width: 480px) {
  h1 {
    font-size: 36px;
  }

  button {
    min-width: 180px;
    font-size: 14px;
  }
}

</style>