<script setup>
import Gallery from "@/components/detail/Gallery.vue";
import GalleryDescription from "@/components/detail/GalleryDescription.vue";
import SideGallery from "@/components/detail/SideGallery.vue"
import { ref } from "@vue/reactivity";
import { onMounted, computed } from "vue";
import axios from "axios";
import { useRoute } from 'vue-router';

const route = useRoute();
const item = ref({});
let defaultImage = ref({});

async function getProduct() {
  try {
    const response = await axios.get(
      "https://zulkit.viainvitation.com/api/products?id=" +
        route.params.id
    );
    item.value = response.data.data;
    const { thumbnails } = response.data.data;
    const dataThumbnail = {
      thumbnails: thumbnails
    }
    defaultImage = dataThumbnail;
  } catch (error) {
    console.error(error);
  }
}
const features = computed(() => {
  return (item.value.features || "").split(",");
});

onMounted(() => {
  window.scrollTo(0, 0);
  getProduct();
});
</script>

<template>
  <div class="container p-2 mx-auto my-10 max-w-7xl" v-if="item">
    <div class="flex flex-row flex-wrap py-4">
      <main role="main" class="w-full px-4 pt-1 sm:w-2/3 md:w-2/3">
        <h1 class="mb-2 text-3xl font-bold leading-normal tracking-tight text-gray-900 sm:text-4xl md:text-4xl">
          {{ item.name }}
        </h1>
        
        <p class="text-gray-500">{{ item.subtitle }} </p>
        <Gallery :defaultImage="defaultImage" :galleries="item.galleries"/>
        <GalleryDescription :desc="item.description"/>
      </main>
      <SideGallery :figma="item.is_figma" :sketch="item.is_sketch" :features="features" :item="item" />
    </div>
  </div>
</template>
