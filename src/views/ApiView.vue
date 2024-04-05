<script setup>
import { ref } from 'vue';

const products = ref([])
const isError = ref(false)

fetch('https://dummyjson.com/products')
  .then(async (response) => {
    products.value = (await response.json()).products
  })
  .catch(()=> {
    isError.value = true
  })
</script>

<template>
  <h2>Товары для чайников и утюгов</h2>
  <p v-if="isError" class="alert alert-danger">Ошибка получения данных!</p>
  <div v-else class="d-flex flex-wrap p-4 gap-2">
    <div v-for="product in products" :key="product.id" class="card" style="width: 18rem">
      <img class="card-img-top" :src="product.thumbnail" alt="Card image cap">
      <div class="card-body">
        <h5 class="card-title">{{ product.title }}</h5>
        <p class="card-text">{{ product.description }}</p>
      </div>
      <div class="card-footer d-flex align-items-center">
        <p class="fw-bold fst-italic" style="margin: auto 0;">{{ product.price }} чупакабриков</p>
        <RouterLink :to="'/api/' + product.id" style="margin-left: auto;" class="btn btn-primary">Go see</RouterLink>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>