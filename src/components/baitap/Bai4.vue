<template>
<div>
     <button @click="show">Hiện</button>
     <button @click="hide">Ẩn</button> 
     <p v-show="isVisible">Welcome to RikkeiAcademy</p>
</div>
</template>

<script setup>
import { ref } from 'vue'
const isVisible = ref(false);
const show = () => {
    isVisible.value = true;
}
const hide = () => {
    isVisible.value = false;
};

</script>

<style>

</style>