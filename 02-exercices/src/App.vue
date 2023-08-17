<script setup>
import Button from './components/Button.vue';
import Presentation from './components/Presentation.vue';
import { ref } from 'vue';
const total = ref(0);
const handle = (event) => total.value += event;
</script>

<template>
    <div class="container">
        <Presentation />
        {{ total }}
        <Button @incrementBy="handle">Envoyer</Button>
        <Button color="blue" @incrementBy="handle">Commander</Button>
        <Button color="red" @incrementBy="handle">Voir</Button>
    </div>
</template>

<style scoped>
.container {
    max-width: 1000px;
    margin: auto;
}
</style>
