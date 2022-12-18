<script setup>
import { ref } from 'vue';
import FeatureList from "@/components/authentication/FeatureList.vue";
import PriceCard from "@/components/pricing/PriceCard.vue";
const price = ref([
    'IDR',
    '2,000',
    'month'
])
const priceGold = ref([
    'IDR',
    '9,000',
    'month'
])
const priceCheckout = ref(2000);
const priceCheckoutGold = ref(9000);
const titlePlan = ref('Basic Plan')
const goldPlan = ref('Gold Plan')
const descPlan = ref('Suitable for new team')
const descGold = ref('Suitable for big company')
const basicPrice = ref([
    {id: 1, text: "Customizable layers"},
    {id: 2, text: "Official documentation"},
    {id: 3, text: "SVG icons"},
    {id: 4, text: "SVG illustrations"},
    {id: 5, text: "Pre-built design screen"},
])
const goldPrice = ref([
    {id: 1, text: "Customizable layers"},
    {id: 2, text: "Official documentation"},
    {id: 3, text: "SVG icons"},
    {id: 4, text: "SVG illustrations"},
    {id: 5, text: "Pre-built design screen"},
    {id: 6, text: "Coded template"},
    {id: 7, text: "Support 24/7"},
    {id: 8, text: "Private designer group"},
    {id: 9, text: "Unlock cloning app"},
])
</script>

<template>
  <main>
    <div class="relative overflow-hidden bg-white">
      <div class="mx-auto">
        <div
          class="flex flex-col items-center w-full sm:justify-center sm:pt-0"
        >
          <div class="w-full p-5 mx-auto mt-10 md:max-w-7xl">
            <h2 class="mb-4 text-5xl font-bold text-center">
              <span class="block lg:mb-2">Friendly Pricing,</span>
              <span class="block">High Quality Design</span>
            </h2>
            <p class="mb-5 text-lg text-center text-gray-500">
              Working faster and better than before
            </p>
          </div>
          <div class="w-full p-5 mx-auto mb-10 md:max-w-4xl">
            <div class="grid grid-cols-1 gap-12 md:grid-cols-2">
              <PriceCard :price="price" :title-plan="titlePlan" :desc-plan="descPlan" :list-price="basicPrice" :price-checkout="priceCheckout"/>
              <PriceCard :price="priceGold" :title-plan="goldPlan" :desc-plan="descGold" :list-price="goldPrice" :price-checkout="priceCheckoutGold" />
            </div>
          </div>
          <div class="w-full p-5 mx-auto mb-10 md:max-w-7xl">
            <div class="grid grid-cols-1 gap-4 mx-auto md:grid-cols-3 md:mx-0">
              <FeatureList />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
