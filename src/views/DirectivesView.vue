<script setup>
import { ref } from 'vue'

const message = 'Приветствую вас на курсе по изучению университета!'
const authForm = ref({})
const seen = ref(false)
const seen2 = ref(false)
const fruits = ref([
  "Яблоко", "Апельсин", "Груша", "Банан", "Маракуйя", "Папайя", "Мангостан"
])
const students = ref([
  {
    fio: 'Московская Государственная Университетская',
    birth: '1942 г.',
    sex: 'не определён'
  },
  {
    fio: 'Евсеев Дмитрий Витальевич',
    birth: '04.11.2005',
    sex: 'муж.'
  },
  {
    fio: 'Буйкин Андрей Витальевич',
    birth: '20.12.2005',
    sex: 'муж.'
  },
  {
    fio: 'Шейкина Елизавета Викторовна',
    birth: '23.04.2005',
    sex: 'жен.'
  }
])

const bindImage = ref("https://masterpiecer-images.s3.yandex.net/60c772735eb511eebfc2963c1ee369ba:upscaled")
const bindValue = ref("Милый котик")

const formFunc = (data) => alert(JSON.stringify(data))
const click = (color) => alert(`Вы нажали ${color} кнопку!`)
</script>

<template>
  <div class="m-3">
    <h2 class="text-center">{{ message }}</h2>
    <h3>Директива v-model</h3>

    <form @submit.prevent="formFunc(authForm)">
      <input placeholder="Введите логин" v-model="authForm.login" />
      <p>Ваш логин{{ authForm.login ? ': ' + authForm.login : " не указан" }}</p>
    </form>
  </div>

  <div class="m-3">
    <h3>Директива v-if</h3>
    <div v-if="seen">
      <p>Этот блок виден, т.к. переменная seen - Истина</p>
      <p>Второй - убран из DOM-дерева</p>
    </div>
    <div v-else>
      <p>Этот блок виден, т.к. переменная seen - Ложна</p>
      <p>Первый - убран из DOM-дерева</p>
    </div>
    <button class="btn" :class="{ 'btn-success': seen, 'btn-warning': !seen }" @click="seen = !seen">Жмякни и переключи
    </button>
  </div>

  <div class="m-3">
    <h3>Директива v-show</h3>
    <div v-show="seen2">
      <p>Этот блок виден, т.к. переменная seen - Истина</p>
      <p>Второй - скрыт, т.к. к нему добавлен атрибут style, скрывающий его</p>
    </div>
    <div v-show="!seen2">
      <p>Этот блок виден, т.к. переменная seen - Ложна</p>
      <p>Первый - скрыт, т.к. к нему добавлен атрибут style, скрывающий его</p>
    </div>
    <button class="btn" :class="{ 'btn-success': seen2, 'btn-warning': !seen2 }" @click="seen2 = !seen2">Жмякни и переключи
    </button>
  </div>

  <div class="m-3">
    <h3>Директива v-for</h3>
    <p>Список фруктов: </p>
    <ul>
      <li v-for="item in fruits" :key="item">
        {{ item }}
      </li>
    </ul>
  </div>

  <div class="m-3">
    <h3>Директива v-for (массив объектов)</h3>
    <p>Список студентов: </p>
    <ol>
      <li v-for="student in students" :key="student.fio">
        <p>ФИО: <b>{{ student.fio }}</b></p>
        <p>Дата рождения: {{ student.birth }}</p>
        <p>Пол: {{ student.sex }}</p>
      </li>
    </ol>
  </div>

  <div class="m-3">
    <h3>Директива v-bind</h3>
    <div>
      <img :src="bindImage" alt="Картинка" width="300">
      <br>
      <input type="text" :value="bindValue" disabled>
    </div>
  </div>

  <div class="m-3">
    <h3>Директива v-on</h3>
    <button @click="click('зелёную')" class="btn btn-success m-1">Кнопка 1</button>
    <button @click="click('жёлтую')" class="btn btn-warning">Кнопка 2</button>
  </div>
</template>

<style scoped>
input {
  width: 300px;
}
</style>