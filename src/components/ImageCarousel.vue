<script setup>
import { defineProps, ref } from 'vue'
import { ArrowLeftCircleIcon, ArrowRightCircleIcon } from '@heroicons/vue/20/solid'

const props = defineProps({
  activities: Array,
  alt: Array,
  images: Array
})

// Local State
const currentImage = ref(0)

// Function for prev & next images
const changeImage = (direction) => {
  currentImage.value = (currentImage.value + direction + props.images.length) % props.images.length
}
</script>

<template>
  <div class="relative">
    <h2 class="text-2xl text-center font-bold">Activities</h2>

    <img :src="images[currentImage]" :alt="alt[currentImage]" class="w-full  size-60 object-cover rounded-xl my-6" />

    <h3 class="text-lg text-center font-semibold">
      {{ activities[currentImage] }}
    </h3>

    <button class="absolute left-0 top-32 -translate-y-1/2" aria-label="Previous image" @click="changeImage(-1)">
      <ArrowLeftCircleIcon class="h-7 w-7 text-white hover:text-indigo-600" aria-hidden="true" />
    </button>

    <button class="absolute right-0 top-32 -translate-y-1/2" aria-label="Next image" @click="changeImage(1)">
      <ArrowRightCircleIcon class="h-7 w-7 text-white hover:text-indigo-600" aria-hidden="true" />
    </button>
  </div>
</template>
