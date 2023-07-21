<template>
    <div class="root-container">
        <h1>ASSET TREE BROWSER</h1>
        <div class="top-panel">
            <p :style="{ fontSize: '35px' }">Top Panel</p>

            <div class="button">
                <button>Button 1</button>
            </div>
            <div class="button">
                <button>Button 2</button>
            </div>
            <div class="button">
                <button>Button 3</button>
            </div>
            <div class="button">
                <button>Button 3</button>
            </div>
        </div>
        <div class="container-panel">
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
    </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'
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
        name: 'name3',
        id: 2,
        age: 2,
    },
    {
        name: 'name4',
        id: 2,
        age: 2,
    },
    {
        name: 'name4',
        id: 2,
        age: 2,
    },
    {
        name: 'name4',
        id: 2,
        age: 2,
    },
    {
        name: 'name4',
        id: 2,
        age: 2,
    },
    {
        name: 'name4',
        id: 2,
        age: 2,
    },
    {
        name: 'name4',
        id: 2,
        age: 2,
    },
    {
        name: 'name4',
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
    flex-direction: column;
    height: 90vh;
    margin: 10px;
    border: 1px solid yellowgreen;
}
.top-panel {
    border: 1px solid blue;
    margin: 10px;
}
.container-panel {
    /* equivalent a */
    margin: 10px;
    display: flex;

    padding: 20px;
    /* il faut definir de maniere dynamique cette hauteur qui doit correspondre */
    /*  a la hauteur maximale du conteneur parent*/
    max-height: 100%;
    overflow: auto;
    flex-direction: column;
    align-items: stretch;
    gap: 10px;
    justify-content: start;
    border: 1px solid red;
    flex-grow: 1;
}
.container {
    margin: 0;
    display: flex;
    flex-direction: column;
    overflow: auto; /* Remplacez "scroll" par "auto" */
    max-height: max-content;
    /*height: 50vh;*/
    width: auto;
    align-items: start;
    justify-content: start;
    border: 1px solid green;
    &&::-webkit-scrollbar {
        width: 12px; /* Largeur de la barre de défilement */
    }

    &&::-webkit-scrollbar-thumb {
        background-color: blue; /* Couleur de la barre de défilement */
        border-radius: 10px;
        border: 2px solid rgba(0, 0, 255, 0.601);
    }

    &&::-webkit-scrollbar-track {
        background-color: grey; /* Couleur du fond de la barre de défilement */
    }
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
