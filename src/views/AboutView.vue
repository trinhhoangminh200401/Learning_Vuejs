<!-- <template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style> -->

<template>
  <div>
    <!-- <h1 id="count">Count: {{ count }}</h1> -->
    <!-- <button type="button" @click="increament">Increase</button> -->
    <h1>watcher</h1>
    <p> Asked one question you can reply yes or no</p>
    <input v-model="question" :disabled="isLoading">
    <p>{{ answer }}</p>
  </div>
  
</template>

<script setup>
import { onMounted, onBeforeMount, onBeforeUnmount, ref, onUnmounted, onUpdated, onBeforeUpdate, watch } from 'vue';

const question = ref('')
const isLoading = ref(false)
const answer =ref("")
// const count = ref(0)
watch(question, async (newQuestion, OldQuestion) => {
  if (newQuestion.includes('yes?'))
  {

    isLoading.value = true;
    answer.value="Thinking..."
    try {
      const response = await fetch('http://localhost:8000/api/food')
    
       answer.value=  (await response.json())
      
    } catch (error) {
      answer.value="Error! cant call api"
      
    }
    finally {
      isLoading.value=false
    }
  }
  else {
     isLoading.value = true;
    answer.value = "Thinking...";

    setTimeout(() => {
      isLoading.value = false;
       answer.value="no info"

    },500)
  }
  
})
// watch(count, (newValue, Oldvalue) => {
//   console.log('Count change old value to new value',Oldvalue,newValue);
// })

// const increament = () => {
//   count.value++;
// }
// onBeforeUpdate(() => [
//   console.log('before update',document.getElementById("count").textContent)
// ])
// onUpdated(() => {
//   console.log('onUpdated',document.getElementById("count").textContent);
  
// })


</script>