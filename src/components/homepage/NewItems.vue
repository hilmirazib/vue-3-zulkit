<script setup>
import { ref } from '@vue/reactivity';
import { RouterLink } from 'vue-router'
import NewItemCards from './items/NewItemCards.vue';

const categories = ref([
    {id: 1, title: "Mobile UI Kit", description: "Mobile UI Kit", image: "items-1.jpg"},
    {id: 2, title: "Website UI Kit", description: "Online Doctor Consultation", image: "items-2.jpg"},
    {id: 3, title: "Mobile UI Kit", description: "Banking Crypto", image: "items-3.jpg"},
])
</script>
<template>
    <div class="container px-4 mx-auto my-16 md:px-12">
      <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">New Items</h2>
      <div class="flex flex-wrap -mx-1 lg:-mx-4">
        <NewItemCards v-for="category in categories" :key="category.id" :id="category.id" :title="category.title" :description="category.description" :image="category.image"/>
      </div>
    </div>
</template>
