<script setup>
import { ref } from 'vue';
defineProps(['color']);
const emit = defineEmits(['incrementBy']);

const count = ref(0);
const increment = () => {
    count.value++;
    emit('incrementBy', 1);
}
</script>

<template>
    <button @click="increment" :class="color" :style="{ backgroundColor: color }">
        <slot /> {{ count }}
    </button>    
</template>

<style scoped>
button {
    padding: 10px 15px;
    border: 0;
    border-radius: 20px;
    cursor: pointer;
    background-color: #000;
    color: #fff;
}

button.blue {
    background-color: blue !important;
    color: #fff;
}
</style>
