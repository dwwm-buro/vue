<script setup>
import { computed, ref } from 'vue';

const name = ref('Jean');
const age = ref(52);
const gender = ref('girl');
const inTenYears = computed(() => age.value + 10);

const nameValid = computed(() => name.value.length >= 1 && name.value.length <= 15);
const ageValid = computed(() => age.value >= 1 && age.value < 100);

const names = ['Toto', 'Titi', 'Tata', 'Jean', 'Eric', 'Fiorella'];
const generate = () => {
    name.value = names[Math.floor(Math.random() * names.length)];
    age.value = Math.floor(Math.random() * 100);
};

generate();
</script>

<template>
    <h1>TP : Présentation</h1>
    <div class="field">
        <label for="name">Nom: </label>
        <input type="text" v-model="name" id="name" :class="{ 'error-input': !nameValid }">
        <div class="error-message" v-if="!nameValid">Maximum 15 caractères</div>
    </div>
    <div class="field">
        <label for="age">Âge: </label>
        <input type="number" v-model="age" id="age" :class="{ 'error-input': !ageValid }">
        <div class="error-message" v-if="!ageValid">
            Veuillez entrer un âge compris entre 1 et 100
        </div>
    </div>
    <div class="field">
        <label for="gender">Genre: </label>
        <select v-model="gender" id="gender">
            <option value="girl">Fille</option>
            <option value="boy">Garçon</option>
        </select>
    </div>

    <button @click="generate">Générer une personne</button>

    <div class="result" v-if="nameValid && ageValid" :class="{ boy: gender === 'boy', girl: gender === 'girl' }">
        <p>Mon nom est <strong>{{ name }}</strong> et j'ai <strong>{{ age }}</strong> ans.</p>
        <p>Dans 10 ans, j'aurai <strong>{{ inTenYears }}</strong> ans.</p>
        <p>Mon nom se compose de <strong>{{ name.length }}</strong> caractères.</p>
        <p>Mon nom en majuscules est <strong>{{ name.toUpperCase() }}</strong>.</p>
    </div>

    <div v-else class="error">
        Veuillez entrer un nom et un âge valide !
    </div>
</template>

<style scoped>
.field {
    margin-bottom: 20px;
}

.result {
    background-color: lightyellow;
    padding: 10px;
    margin-top: 20px;
}

.result.boy {
    background-color: lightblue;
}

.result.girl {
    background-color: lightpink;
}

.error {
    background-color: lightcoral;
    padding: 10px;
}

.error-message {
    color: lightcoral;
}

.error-input {
    background-color: lightcoral;
    border-color: red;
}
</style>
