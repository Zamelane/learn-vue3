<script setup>
import Logo from '@/components/icons/Logo.vue'
</script>

<template>
  <section class="d-flex flex-column justify-content-center align-items-center m-4">
    <div class="start">
      <h2>Учим Мгу3!</h2>
      <p>Типа крутой университет</p>
      <Logo/>
      <br>
      <RouterLink to="/directives" class="btn btn-success">
        Начать обучение
      </RouterLink>
    </div>
  </section>
</template>