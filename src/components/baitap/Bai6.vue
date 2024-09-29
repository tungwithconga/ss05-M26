<template>
  <div>
    <p>Danh sách các số thoả mãn điều kiện:</p>
    <ul>
      <li v-for="number in filteredNumbers" :key="number">{{ number }}</li>
    </ul>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const numbers = ref([5, 12, 15, 22, 9, 18, 25, 30, 7, 33]);

const filteredNumbers = computed(() => {
  return numbers.value.filter(number => number > 10 && number % 2 !== 0);
});
</script>

<style scoped>

</style>
