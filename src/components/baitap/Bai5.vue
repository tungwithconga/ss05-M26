<template>
  <div>
    <p>Các số chẵn từ mảng:</p>
    <ul>
      <li v-for="number in evenNumbers" :key="number">{{ number }}</li>
    </ul>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const numbers = ref([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);

const evenNumbers = computed(() => {
  return numbers.value.filter(number => number % 2 === 0);
});
</script>

<style scoped>
</style>
