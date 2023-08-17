<script setup>
import { computed, ref } from 'vue';

const message = ref('Hello');
const name1 = ref('Fiorella');
const reversed = computed(() => {
    console.log('computed');
    return message.value.split('').reverse().join('');
});

const name = ref('Mota');
const firstname = ref('Fiorella');

const fullName = computed({
    get: () => `${firstname.value} ${name.value}`,
    set: (value) => {
        let names = value.split(' '); // 'Fiorella Mota' => ['Fiorella', 'Mota']

        firstname.value = names[0] ?? '';
        name.value = names[1] ?? '';
    }
});
</script>

<template>
    <h2>Computed</h2>
    <p>{{ message }} à l'envers {{ reversed }}</p>
    <input type="text" v-model="message">
    <input type="text" v-model="name1">

    <input type="text" v-model="fullName">
    <p>{{ fullName }}</p>
    <p>Prénom: {{ firstname }}, Nom: {{ name }}</p>
</template>
