<script setup>
import { ref, onMounted, computed } from 'vue'

const list = ref([
    {
    id:1
},  {
    id:1
},
])
const { firstName, lastName, isActive } = defineProps({firstName:String , lastName:String,isActive:Boolean})
// const fullName = computed(() => firstName + lastName)

const itemRefs = ref([])
onMounted(() => console.log(itemRefs.value))
   console.log(firstName + lastName)
 </script>

<template>
  <ul>
    <li v-for="item in list"  class="actibe" ref="itemRefs">
      {{ item.id }}
    </li>
    {{ isActive ? `${firstName} ${lastName}` : 'Toggle is delete' }}        
  </ul>
</template>