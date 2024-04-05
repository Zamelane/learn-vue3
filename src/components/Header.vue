<script setup>
import { RouterLink } from 'vue-router';

const links = [
  {
    name: "Главная",
    path: '/'
  },
  {
    name: "Знакомство с директивами",
    path: '/directives'
  },
]

</script>

<template>
  <header>
    <nav class="navbar navbar-dark bg-dark">
      <ul class="d-flex">
        <li v-for="(item, index) in links" :key="index" class="nav-item m-3">
          <RouterLink :to="item.path" class="nav-link">{{ item.name }}</RouterLink>
        </li>
      </ul>
    </nav>
  </header>
</template>

<style scoped>
li {
  list-style-type: none;
}

a {
  color: whitesmoke;
}

a:hover {
  color: #5599ee;
}
</style>