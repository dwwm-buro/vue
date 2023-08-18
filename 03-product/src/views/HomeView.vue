<script setup>
import { computed, ref, watch } from 'vue';
const product = ref({
  name: 'Cat',
  brand: 'Brand',
  stock: 10,
  features: ['Mignon', 'Affectueux', 'Gourmand'],
  image: 'https://cdn2.thecatapi.com/images/EhOq2RbaI.jpg',
  price: 10,
  variations: [
    { color: 'blue' },
    { color: 'red' }
  ],
});
const quantity = ref(1);

const title = computed(() => product.value.brand + ' ' + product.value.name);
const price = computed(() => {
  return new Intl.NumberFormat('fr-FR', { style: 'currency', currency: 'EUR' }).format(product.value.price * quantity.value);
});

watch(quantity, (newQty, oldQty) => {
  if (newQty > Math.floor(product.value.stock / 2)) {
    alert(`Attention, il reste ${product.value.stock - newQty} produits.`);
  }
});
</script>

<template>
  <div class="flex">
    <img :src="product.image" :alt="product.name">
    <div>
      <h1>{{ title }}</h1>
      <p class="price">{{ price }}</p>
      <input type="number" v-model="quantity" min="0"
        :max="product.stock" :disabled="product.stock <= 0">
      <p class="in-stock" v-if="product.stock > 0">En stock</p>
      <p class="out-stock" v-else>Pas de stock</p>

      <ul>
        <li v-for="(feature, index) in product.features" :key="index">
          {{ feature }}
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.flex {
  display: flex;
  gap: 30px;
  max-width: 1000px;
  margin: auto;
}

img {
  width: 50%;
}

.price {
  margin: 20px 0;
  font-size: 20px;
}

input {
  padding: 10px;
  border-radius: 10px;
  font-size: 20px;
  border: 2px solid lightgray;
  text-align: center;
  width: 100%;
  margin-bottom: 10px;
}

.in-stock {
  color: green;
}

.out-stock {
  color: lightcoral;
}

ul {
  margin-top: 20px;
  list-style: none;
}
</style>
