<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import TourismCard from './components/TourismCard.vue'
import tourismInfos from './data/tourismInfos'
</script>

<template>
  <div class="flex flex-col h-screen justify-between">
    <Header />

    <div class="container mx-auto">
      <div class="flex justify-center">
        <TourismCard v-for="(destination, index) in tourismInfos.destinations" :key="index"
          :badgeName="destination.badge" :coverAlt="destination.altImage" :coverImage="destination.coverImage"
          :destinationName="destination.city" :shortDescription="destination.description"
          :activities="destination.activities" :images="destination.images"
          :imagesDescription="destination.imagesDescription" :reviews="destination.reviews" />
      </div>
    </div>

    <Footer />
  </div>
</template>
