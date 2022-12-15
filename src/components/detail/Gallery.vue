<script>
import { ref } from "vue";
export default {
    props: {
        defaultImage: {
        type: Object,
            default: function() {
                return {
                    thumbnails: "",
                }
            }
        },
        galleries: Array,
    },
    data() {
        return {
            thumbnail: ""
        }
    },
    watch: {
        defaultImage: function() {
            this.thumbnail = this.defaultImage.thumbnails;
        }
    },  
    methods: {
        changeImage(image) {
            this.thumbnail = image;
        }
    }
}

</script>

<template>
    <section id="gallery">
        <img :src="thumbnail" alt="" class="w-full mt-6 rounded-2xl">
        <div class="grid grid-cols-4 gap-4 mt-4">
            <template v-for="gallery in galleries" :key="gallery.id">
                <div class="overflow-hidden cursor-pointer rounded-2xl"
                    :class="{ 'ring-2 ring-indigo-500': thumbnail === gallery.url }">
                    <img :src="gallery.url" class="w-full" alt="" @click="changeImage(gallery.url)">
                </div>
            </template>
        </div>
    </section>
</template>
