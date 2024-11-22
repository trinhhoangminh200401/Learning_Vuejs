<script lang="js" setup>
const prop = defineProps({
    id: Number,
    name: String,
    age:Number,
 })
const { id,name,age } = prop


</script>
<template>
    {{ name }}

    </template>