<script setup>
import { ref } from '@vue/reactivity';
import { onMounted } from 'vue'
import { RouterLink } from 'vue-router'
import NewItemCards from './items/NewItemCards.vue';
import axios from 'axios'

// const categories = ref([
//     {id: 1, title: "Mobile UI Kit", description: "Mobile UI Kit", image: "items-1.jpg"},
//     {id: 2, title: "Website UI Kit", description: "Online Doctor Consultation", image: "items-2.jpg"},
//     {id: 3, title: "Mobile UI Kit", description: "Banking Crypto", image: "items-3.jpg"},
// ])

const items = ref([])

async function getItemsData() {
    try {
        const response = await axios.get('https://zulkit.viainvitation.com/api/products')
        items.value = response.data.data.data
    } catch (error) {
        console.error(error)
    }   
}

onMounted(() => {
    getItemsData()
})
</script>
<template>
    <div class="container px-4 mx-auto my-16 md:px-12">
      <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">New Items</h2>
      <div class="flex flex-wrap -mx-1 lg:-mx-4">
        <NewItemCards v-for="item in items" :key="item.id" :id="item.id" :title="item.name" :description="item.subtitle" :image="item.thumbnails"/>
      </div>
    </div>
</template>
