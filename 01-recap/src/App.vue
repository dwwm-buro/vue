<script setup>
import Computed from './components/Computed.vue';
import Exercice1 from './components/Exercice1.vue';
import Image from './components/Image.vue';
import { ref } from 'vue';

const count = ref(0);
const increment = (number, event) => {
  count.value += number;
  console.log(event);
};

const color = ref('red');
const displayText = (event) => alert(event.target.value);
</script>

<template>
  <h1>Hello Vue {{ count }}</h1>
  <button @click="increment(1, $event)" v-if="count < 10">Incrémenter</button>
  <button @click="increment(-1)" :disabled="count <= -10">Décrémenter</button>
  <input type="text" v-model="count">
  <Image source="a042581f4e29026704d" />
  <Image source="abc" />
  <Image :source="Math.random()" />

  <Exercice1 />

  <input type="text" v-model="color">

  <div :style="{ backgroundColor: color }">
    Un texte
  </div>
  <input type="text" @keyup.enter="displayText">

  <Computed />
</template>

<style scoped>
button {
  background-color: lightblue;
  border: 0;
  cursor: pointer;
}
</style>
