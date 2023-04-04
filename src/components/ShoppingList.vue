<script setup lang="ts">
import { ref } from 'vue';

const header = ref<string>('Shopping List')
const newItem = ref<string>('')


const items = ref<{
    id: number;
    label: string;

}[]>([
    {id: 1, label: "3 paket kaffe"},
    {id: 2, label: "Kakor"},
    {id: 3, label: "Hundmat"},
    {id: 4, label: "Toalettpapper"}
])

const addItem = () => {
    items.value.push({id: items.value.length + 1, label: newItem.value })
    newItem.value = ""
}

</script>

<template>
    <section class="border-black flex flex-col bg-slate-400 w-full p-8 gap-2">
        <h1 class="text-black-500	text-4xl ">{{ header }}</h1>
        <form  @submit.prevent="addItem">
            <input
                v-model.number="newItem"
                type="text"
                placeholder="Add an item"
                class="rounded px-1">
            <button>Save item</button>
        </form>
    
        <ul class="flex flex-col">
            <li v-for="{id, label} in items" :key="id"
            class="self-start">{{ label }}</li>
        </ul>
    </section>

</template>