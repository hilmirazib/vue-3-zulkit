<script setup>
import { computed } from "vue";
import { useUserStore } from "@/stores/user";
const props = defineProps({
  figma: Number,
  sketch: Number,
  features: Array,
  item: Object
});
const userStore = useUserStore();
const user = computed(() => userStore.getUser);
</script>

<template>
  <aside class="w-full px-4 sm:w-1/3 md:w-1/3">
    <div class="sticky top-0 w-full pt-4 md:mt-24 ">
      <div class="p-6 border rounded-2xl">
        <div class="mb-4" v-if="figma == 1">
          <div class="flex mb-2">
            <div>
              <img src="@/assets/img/icon-figma.png" alt="" class="w-16" />
            </div>
            <div class="block mt-1 ml-4">
              <h3 class="font-semibold text-md">Figma {{user.subscription}}</h3>
              <p class="text-gray-400 text-md">Project Included</p>
            </div>
          </div>
        </div>
        <div class="mb-4" v-if="sketch == 1">
          <div class="flex mb-2">
            <div>
              <img src="@/assets/img/icon-sketch.png" alt="" class="w-16" />
            </div>
            <div class="block mt-1 ml-4">
              <h3 class="font-semibold text-md">Sketch</h3>
              <p class="text-gray-400 text-md">Project Included</p>
            </div>
          </div>
        </div>
        <div>
          <h1 class="mt-5 mb-3 font-semibold text-md">Great Features</h1>
          <ul class="mb-6 text-gray-500">
            <li class="mb-2" v-for="feature in features">
              {{ feature }}
              <img src="@/assets/img/icon-check.png" class="float-right w-5 mt-1" alt="" />
            </li>
          </ul>
        </div>
        <!-- <div v-if="user"> -->
          <a v-if="user.subscription !== undefined && user.subscription.length > 0" :href="item.file" class="
                    inline-flex
                    items-center
                    justify-center
                    w-full
                    px-8
                    py-3
                    text-base
                    font-medium
                    text-white
                    bg-indigo-600
                    border border-transparent
                    rounded-full
                    hover:bg-indigo-700
                    md:py-2 md:text-md md:px-10
                    hover:shadow
                  ">
            Download Now
          </a>
        <!-- </div> -->
        <RouterLink to="/pricing" v-else
          class="inline-flex items-center justify-center w-full px-8 py-3 text-base font-medium text-white bg-indigo-600 border border-transparent rounded-full hover:bg-indigo-700 md:py-2 md:text-md md:px-10 hover:shadow">
          Subscribe
        </RouterLink>
      </div>
    </div>
  </aside>
</template>
