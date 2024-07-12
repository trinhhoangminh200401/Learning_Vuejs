<template>
  <div>
    <h1>{{ message }}</h1>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

 
    const message = ref('Hello from Child Component!');

    onMounted(() => {
      console.log('ChildComponent has been mounted!');
    });

    onUnmounted(() => {
      console.log('ChildComponent has been unmounted!');
    });



</script>
