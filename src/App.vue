<template>
    <div class="root-container">
        <button @click="toggle">Plus</button>
        <div class="container">
            <Item
                v-if="isShown"
                :item="data"
                class="item-container"
                v-for="data in datas"
                :key="data.id"
            />
            <Item
                v-else
                :item="datas[0]"
                class="item-container"
                :key="datas[0].id"
            />
        </div>
    </div>
</template>

<script setup lang="ts">
import { reactive, ref, computed } from 'vue'
import Item from './components/Item.vue'
interface Item {
    name: string
    id: number
    age: number
}
const isShown = ref<boolean>(false)
const datas = reactive<Item[]>([
    {
        name: 'name',
        id: 1,
        age: 1,
    },
    {
        name: 'name2',
        id: 2,
        age: 2,
    },
    {
        name: 'name2',
        id: 2,
        age: 2,
    },
    {
        name: 'name2',
        id: 2,
        age: 2,
    },
])

const toggle = () => {
    isShown.value = !isShown.value
}
</script>

<style scoped>
.root-container {
    display: flex;
    padding: 20px;
    flex-direction: column;
    align-items: start;
    justify-content: center;
    border: 1px solid red;
}
.container {
    margin: 0;
    display: flex;
    flex-direction: column;
    overflow: auto; /* Remplacez "scroll" par "auto" */
    height: 400px;
    width: 300px;
    align-items: start;
    justify-content: start;
    border: 1px solid green;
}
.button {
    margin: 20px;
    height: auto;

    &:hover {
        cursor: pointer;
    }
    .item-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        border: 1px solid blue;
        padding: 20px;
        margin: 20px;
    }
}
</style>
