<script setup>
  import { ref } from 'vue';

  let title = 'Recettes';
  const recettes = ref(['Couscous', 'Fondue', 'Salade César', 'Sandwich']);
  const show = ref(true);
  const toggle = () => show.value = !show.value;
</script>

<template>
  <h1>{{ title }}</h1>
  <ul v-if="show">
    <li v-for="meal in recettes">
      {{ meal }}
    </li>
  </ul>
  <button @click="toggle">Afficher / Cacher la liste</button>
  <input type="checkbox" v-model="show">
</template>

<style scoped>
</style>
