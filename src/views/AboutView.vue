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
    <!-- <input v-model="question" :disabled="isLoading">
    <p>{{ answer }}</p> -->
    <p>{{ x }},{{ y }}</p>
    <button type="button" @click="increament">Increase</button>
    <button type="button" @click="changeAge">change age</button>
    <p>{{ user.age }}</p>
  </div>
  
</template>

<script setup>
import { onMounted, onBeforeMount, onBeforeUnmount, ref, onUnmounted, onUpdated, onBeforeUpdate, watch, reactive, watchEffect } from 'vue';

const user = reactive({

  age: 18,
  class: {

    student: 0,
    name:'Minh'
    
  }
})

const x = ref(0)
const y = ref(0)
watch([x, y], ([newUser, oldUser]) => {
      console.log('Giá trị sau n ::',newUser,oldUser)

},{immediate:true})


watch(() => x.value + y.value, async (sum) => {
  console.log('Sum x + y:',sum)
})
const increament = () => {
  x.value++;
  y.value++;
}
watch([x, () => y.value + 1], ([newX, newY]) => {

  console.log('Update data:',newX,newY)
  
})
watch(()=>user.age, (newAge) => {
  console.log(`Tuổi: ${newAge}`)
})

watch(user,
  (newUser,oldUser) => {
    console.log(`User: newUser ${JSON.stringify(newUser)},oldUser ${JSON.stringify(oldUser)}`)
  }
  , { deep: true, immediate: true })
watchEffect(() => (
    console.log('Giá trị sau n ',x.value,y.value)

))
const changeAge = () => {
  user.class.student++
}


/* ---------------------------------- watch ----------------*/

// const question = ref('')
// const isLoading = ref(false)
// const answer =ref("")
// const count = ref(0)
// watch(question, async (newQuestion, OldQuestion) => {
//   if (newQuestion.includes('yes?'))
//   {

//     isLoading.value = true;
//     answer.value="Thinking..."
//     try {
//       const response = await fetch('http://localhost:8000/api/food')

//        answer.value=  (await response.json())

//     } catch (error) {
//       answer.value="Error! cant call api"

//     }
//     finally {
//       isLoading.value=false
//     }
//   }
//   else {
//      isLoading.value = true;
//     answer.value = "Thinking...";

//     setTimeout(() => {
//       isLoading.value = false;
//        answer.value="no info"

//     },500)
//   }

// })
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
// 
/* ---------------------------------- exmaple 2  ----------------*/


</script>