
<script setup>
import { RouterLink } from 'vue-router'
defineProps({
    price: Array,
    titlePlan: String,
    descPlan: String,
    listPrice: Array
})
</script>
<template>
    <div>
        <div class="p-8 border rounded-3xl">
            <h1 class="text-5xl font-semibold">
                {{ `${price[0]} ${price[1]}` }} <span class="text-xl font-light text-gray-500">/{{price[2]}}</span>
                <!-- IDR 2,000 <span class="text-xl font-light text-gray-500">/month</span> -->
            </h1>
            <h2 class="text-lg font-semibold mt-7">{{ titlePlan }}</h2>
            <p class="mb-6 text-gray-500">{{ descPlan }}</p>
            <ul class="mb-6 text-gray-700">
                <li class="mb-3" v-for="list in listPrice" :key="list.id">
                    <img src="@/assets/img/icon-check.png" class="float-left w-6 mr-2" alt="" />{{ list.text }}
                </li>
            </ul>
            <RouterLink to="/success"
                class="inline-flex items-center justify-center w-full px-8 py-3 text-base font-medium text-black bg-gray-200 border border-transparent rounded-full hover:bg-gray-300 md:py-2 md:text-md md:px-10 hover:shadow">
                Checkout Now
            </RouterLink>
        </div>
    </div>
</template>
