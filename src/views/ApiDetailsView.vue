<script setup>
import { useRouter } from 'vue-router';
import { ref } from 'vue';

const router = useRouter()
const product = ref([])
const isError = ref(false)

const id = router.currentRoute.value.params.id

fetch('https://dummyjson.com/products/' + id)
  .then(async (response) => {
    product.value = (await response.json())
  })
  .catch(()=> {
    isError.value = true
  })

</script>

<template>
  <p v-if="isError" class="alert alert-danger">Произошла ошибка!</p>
  <div v-else class="d-flex flex-column">
    <b>{{ product.title }}</b>

    <p>Описание товара: {{ product.description }}</p>

    <div class="mb-3 p-1">
      <p class="mb-0 fst-italic">Галерея</p>
      <div class="d-flex gap-2 flex-wrap" v-if="product.images">
        <img v-for="image in product.images" :src="image" width="200" class="border">
      </div>  
    </div>

    <button type="button" class="btn btn-primary" style="max-width: 10rem;">
      Купить за <b>${{ product.price }}</b>
    </button>
  </div>
</template>