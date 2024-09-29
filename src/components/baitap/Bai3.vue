<template>
  <div>
    <p>Nếu <strong>userRole</strong> = {{ userRole }}</p>
    <p>Quyền hạn của bạn là: <strong>{{ displayRole }}</strong></p>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const userRole = ref('user');

const displayRole = computed(() => {
  if (userRole.value === 'admin') {
    return 'Admin';
  } else if (userRole.value === 'user') {
    return 'User';
  } else if (userRole.value === 'guest') {
    return 'Guest';
  }
});
</script>

<style scoped>

</style>
