<script setup>
import { defineProps, ref } from 'vue'
import CardRatings from './CardRatings.vue'
import ImageCarousel from './ImageCarousel.vue'

const props = defineProps({
  badgeName: String,
  coverAlt: String,
  coverImage: String,
  destinationName: String,
  shortDescription: String,
  activities: Array,
  images: Array,
  imagesDescription: Array,
  reviews: Object
})

// Local State
const showDetails = ref(false)

function beforeEnter(el) {
  el.style.opacity = 0
  el.style.transform = 'translateY(-10px)' // Initial position for fadeInDown
}

function enter(el, done) {
  el.offsetHeight; // Trigger a reflow
  el.style.transition = 'opacity 0.5s ease-in-out, transform 0.5s ease-in-out';
  el.style.opacity = 1;
  el.style.transform = 'translateY(0)';
  done(); // Call this function when the animation is done
}

function leave(el, done) {
  el.style.transition = 'opacity 0.5s ease-in-out, transform 0.5s ease-in-out';
  el.style.opacity = 0;
  el.style.transform = 'translateY(10px)'; // Position for fadeInUp
  done(); // Call this function when the animation is done
}
</script>

<template>
  <div class="flex flex-col items-end m-12 rounded-xl overflow-hidden shadow-2xl">
    <img :src="coverImage" :alt="coverAlt" class="size-72 w-full object-cover" />

    <div class="my-6 px-6">
      <div class="sm:flex sm:justify-between sm=items-center">
        <h2 class="text-ellipsis font-bold text-xl sm:text-3xl sm:mb-2">{{ destinationName }}</h2>
        <span class="inline-flex h-6 items-center rounded-lg bg-red-500 p-2 text-xs font-medium text-white">
          {{ badgeName }}
        </span>
      </div>

      <p class="mt-6 sm:mt-0 text-gray-700">{{ shortDescription }}</p>

      <div class="sm:flex sm:items-center sm:justify-between mt-6">
        <button @click="showDetails = !showDetails"
          class="px-4 py-2 text-white rounded-lg transition transform ease-in-out delay-0 bg-indigo-600 hover:scale-110 hover:bg-indigo-900">
          {{ showDetails ? "See less" : "See more" }}
        </button>

        <CardRatings :reviews="reviews" />
      </div>

      <transition @before-enter="beforeEnter" @enter="enter" @leave="leave">
        <div v-if="showDetails && images.length > 1" class="transition-all">
          <ImageCarousel :activities="activities" :alt="imagesDescription" :images="images" />
        </div>
      </transition>
    </div>
  </div>
</template>
