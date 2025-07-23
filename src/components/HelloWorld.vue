<template>
    <div>{
        <h1>{{ result }}</h1>
        <h2>{{ counter }}</h2>

        <button @click="increase">+1</button>
        <button @click="decrease">-1</button>
    </div>
</template>

<script setup> 
import { onMounted, ref, onUpdated, computed, watch } from 'vue';

const counter = ref(0);
const result = computed (() => {
    return 'Counter New value :>>' + counter.value
})

watch(counter, () => {
    console.log('counter :>>', counter);
})
const increase = () => {
    counter.value +=1;
}

const decrease = () => {
    counter.value -=1;
}
</script>

<style scoded></style>