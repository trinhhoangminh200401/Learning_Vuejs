<!-- <script setup>
import TheWelcome from '../components/TheWelcome.vue'
</script>

<template>
  <main>
    <TheWelcome />
  </main>
</template> -->
<script setup>
import { ref } from 'vue'

const text = ref('hello')

const checkBox = ref([])
const multiLineText = ref('')
const radioCheck = ref('')
const select = ref('A')
</script>

<template>
  <div>
    <h1>form input</h1>
    <p>{{ text }}</p>
    <input v-model="text" />
    <p>TextArea Text:{{ multiLineText }}</p>
    <textarea v-model="multiLineText" />
    <p>checkbox Text:{{ checkBox }}</p>
    <input v-model="checkBox" type="checkbox" value="Minh" />

    <input v-model="checkBox" type="checkbox" value="Nam" />
    <input v-model="checkBox" type="checkbox" value="Mark" />

    <p>Radio button:{{ radioCheck }}</p>
    <input type="radio" v-model="radioCheck" value="A" />
    <input type="radio" v-model="radioCheck" value="B" />

    <p>Select :{{ select }}</p>
    <select v-model="select">
      <option value="A">A</option>
      <option value="B">B</option>

      <option value="C">C</option>
    </select>
  </div>
</template>
