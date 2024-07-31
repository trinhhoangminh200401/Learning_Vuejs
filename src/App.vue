<script setup>
import { ref } from 'vue'
import HomeView from './views/HomeView.vue'
import AboutView from './views/AboutView.vue'
import CheckView from './views/CheckView.vue'
import ParentView from './views/ParentView.vue'
import RefView from './views/RefView.vue'
// const isActive = ref(true)
// const newTodo = ref('')
// const age = ref(0)
// const todos = ref([
//   {
//     id: 1,
//     age: 23,
//     name: 'Minh'
//   },
//   {
//     id: 2,
//     age: 24,
//     name: 'Mark'
//   }
// ])
// const addTodo = () => {
//   if (newTodo.value.trim() === '') return
//   else {
//     const todo = {
//       id: todos.value.length + 1,
//       age: age.value++,
//       name: newTodo.value
//     }
//     if (todo.name == '') {
//       return []
//     }
//     console.log(todo)
//     todos.value.push(todo)

//     newTodo.value = ''
//   }
// }
const isActive = ref(false)
const handleCLickButton = () => {
  isActive.value = !isActive.value
}
</script>

<template>
  <div>
    <!-- <input type="text" v-model="newTodo" @keyup.enter="addTodo" />
    <ul>
      <li v-for="todo in todos" :key="todo.id">{{ todo.name }}</li>
    </ul> -->
  </div>
  <button @click="handleCLickButton">Toggle</button>
  <RefView firstName="minh" lastName="nnn" :isActive="isActive" />

  <ParentView />
</template>

<style>
.button {
  border: none;
  background: #273672;
  color: red;
  padding: 10px 14px;
  border-radius: 6px;
  cursor: pointer;
  &:hover {
    background: #722771;
  } 
}
.active {
  background: green;
  color: white;
  &:hover {
    background: #243323;
  }
}
</style>
