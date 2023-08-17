<script setup>
const props = defineProps(['start', 'max']);
import { ref } from 'vue';

const count = ref(props.start || 0);
const decrement = () => count.value--;
const increment = () => count.value++;
const color = computed(() => {
    if (count.value >= max) {
        return 'red';
    } else {
        return '';
    }
})
</script>

<template>
    <div class="flex" :style="{ backgroundColor: color }">
        <button @click="decrement" :disabled="count <= 0">-</button>
        <span>{{ count }}</span>
        <button @click="increment" v-if="!max || count < max">+</button>
    </div>
</template>

<style scoped>
.flex {
    display: flex;
    align-items: center;
    gap: 10px;
    justify-content: center;
    margin-bottom: 20px;
    max-width: 200px;
}

button {
    background-color: aqua;
    border: 0;
    padding: 10px;
    cursor: pointer;
    border-radius: 25px;
}

button:disabled {
    opacity: 0.25;
}
</style>
