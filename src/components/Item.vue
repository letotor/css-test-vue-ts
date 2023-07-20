<template>
    <div class="item-container">
        <h1>{{ item.name }}</h1>
        <h2>{{ item.id }}</h2>
        <h3>{{ item.age }}</h3>
    </div>
</template>

<script setup lang="ts">
defineProps<{
    item: {
        name: string
        id: number
        age: number
    }
}>()
</script>

<style scoped>
.item-container {
    display: flex;
    flex-direction: column;
    height: auto;
    max-height: 200px;
    width: 150px;
    flex-wrap: wrap;
    align-items: center;

    border: 1px solid blue;
    padding: 20px;
    margin: 20px;
}
</style>
