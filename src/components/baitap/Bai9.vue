<template>
  <div>
    <button @click="randomGender">Random gender</button>

    <p>Giới tính: {{ selectedGender }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const genders = ['Nam', 'Nữ', 'Khác'];

const selectedGender = ref('Nam');

const randomGender = () => {
  const randomIndex = Math.floor(Math.random() * genders.length);
  selectedGender.value = genders[randomIndex];
};
</script>

<style scoped>
button {
  padding: 10px;
  border: 1px solid black;
  background-color: white;
  color: black;
  cursor: pointer;
  margin-bottom: 10px;
}

p {
  font-size: 18px;
  font-weight: bold;
}
</style>
