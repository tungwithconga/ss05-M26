<template>
  <div>
    <button @click="sortAscending">Tăng dần</button>
    <button @click="sortDescending">Giảm dần</button>
    <div>
      <span v-for="(number, index) in numbers" :key="index" class="number-box">{{ number }}</span>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const numbers = ref([5, 2, 9, 1, 5, 6]);

const sortAscending = () => {
  numbers.value.sort((a, b) => a - b);
};

const sortDescending = () => {
  numbers.value.sort((a, b) => b - a);
};
</script>

<style scoped>
button {
  margin-right: 10px;
  padding: 10px;
  border: 1px solid black;
  background-color: white;
  color: black;
  cursor: pointer;
}

.number-box {
  display: inline-block;
  margin: 5px;
  padding: 10px;
  border: 1px solid black;
  width: 30px;
  text-align: center;
}
</style>
