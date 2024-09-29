<template>
  <div>
    <p v-if="isShow">RikkeiAcademy</p>
    <p v-else></p>
    <button @click="handleToggle">Hiện</button>
  </div>
</template>

<script setup>
import { ref } from "vue";
const isShow = ref(true);
const handleToggle = () => {
  isShow.value = !isShow.value;
};
</script>

<style>

</style>