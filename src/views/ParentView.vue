<template>
  <div id="app">
    <button @click="toggleChildComponent">
      {{ showChildComponent ? 'Hide' : 'Show' }} Child Component
    </button>
    <CheckView v-if="showChildComponent" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import CheckView from './CheckView.vue'

const showChildComponent = ref(true)

const toggleChildComponent = () => {  
  showChildComponent.value = !showChildComponent.value
}
</script>
