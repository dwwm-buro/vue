<script setup>
import Button from './components/Button.vue';
import Counter from './components/Counter.vue';
import Presentation from './components/Presentation.vue';
import { ref } from 'vue';
const total = ref(0);
const handle = (event) => total.value += event;
</script>

<template>
    <div class="container">
        <Presentation />

        <h2>Exemple avec le emit</h2>
        {{ total }}
        <Button @incrementBy="handle">Envoyer</Button>
        <Button color="blue" @incrementBy="handle">Commander</Button>
        <Button color="red" @incrementBy="handle">Voir</Button>

        <h2>TP : Composant Counter</h2>

        <Counter />
        <Counter :start="12" :max="20" />
        <Counter :start="4" :max="20" />
        <Counter :start="17" :max="30" />
    </div>
</template>

<style scoped>
.container {
    max-width: 1000px;
    margin: auto;
}
</style>
