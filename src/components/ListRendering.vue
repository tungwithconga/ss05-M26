<template>
  <div>
    <h1>List Rendering</h1>
    <ul v-for="user in listUser" :key="user.id">
        <li>
            <span>ID:{{ user.id }}</span>
            <span>Name:{{ user.name }}</span>
        </li>
    </ul>
  </div>
</template>

<script setup>
const listUser = [
    {
        id:1,
        name:"Nguyen Van A",
    },
    {
        id:2,
        name:"Nguyen Van B",
    },
    {
        id:3,
        name:"Nguyen Van C",
    },
]
</script>

<style>

</style>