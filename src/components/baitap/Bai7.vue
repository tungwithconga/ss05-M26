<template>
  <div>
    <button
      v-for="(button, index) in buttons"
      :key="index"
      :class="{'active': activeIndex === index + 1}" 
      @click="setActive(index + 1)"
    >
      {{ button }}
    </button>
    <p>Khi nhấn Button {{ activeIndex }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const buttons = ['Button 1', 'Button 2', 'Button 3'];

const activeIndex = ref(1);

const setActive = (index) => {
  activeIndex.value = index;
};
</script>

<style scoped>
button {
  padding: 10px;
  margin: 5px;
  border: 1px solid black;
  background-color: white;
  color: black;
  cursor: pointer;
}

button.active {
  background-color: red;
  color: #fff;
}
</style>
