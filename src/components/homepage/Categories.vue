<script setup>
import { ref } from '@vue/reactivity';
import { onMounted } from 'vue';
import { RouterLink } from 'vue-router'
import CategoryCards from './items/CategoryCards.vue';
import axios from 'axios'

// const categories = ref([
//     {id: 1, title: "Mobile UI Kit", count: 731, image: "categories-1.jpg"},
//     {id: 2, title: "Fonts", count: 658, image: "categories-2.jpg"},
//     {id: 3, title: "Icon Set", count: 8000, image: "categories-3.jpg"},
//     {id: 4, title: "Website UI Kit", count: 1800, image: "categories-4.jpg"},
// ])
const categories = ref([])

async function getCategoriesData() {
    try {
        const response = await axios.get('https://zulkit.viainvitation.com/api/categories?limit=10000')
        categories.value = response.data.data.data
    } catch (error) {
        console.error(error)
    }   
}

onMounted(() => {
    getCategoriesData()
    console.log(categories.value)
})
</script>
<template>
    <div class="container px-4 mx-auto my-16 md:px-12" id="categories">
        <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">Top Categories</h2>
        <div class="flex flex-wrap -mx-1 lg:-mx-4">
            <CategoryCards v-for="category in categories" :key="category.id" :id="category.id" :title="category.name" :count="category.products_count" :image="category.thumbnails"/>
        </div>
    </div>
</template>
