<template>
  <button @click="toggleShow">
    {{ isShow ? 'Ẩn' : 'Hiện' }}
  </button>
</template>

<script setup>
import { ref } from 'vue'

const isShow = ref(false)

const toggleShow = () => {
  isShow.value = !isShow.value
}
</script>
