<template>
  <div>
    <button @click="addRandomNumber">Random number</button>

    <ul>
      <li v-for="(number, index) in numbers" :key="index">{{ number }}</li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const numbers = ref([]);

const addRandomNumber = () => {
  const randomNumber = Math.floor(Math.random() * 100) + 1;
  numbers.value.push(randomNumber);
};
</script>

<style scoped>
button {
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid black;
  background-color: white;
  color: black;
  cursor: pointer;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 5px 0;
  padding: 5px;
  border: 1px solid black;
  width: 50px;
  text-align: center;
}
</style>
