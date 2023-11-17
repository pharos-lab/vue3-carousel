<template>
  <div class="p-8">
    <Carousel class="bg-red-100">
      <Slide class="bg-green-100" :index="0">1</Slide>
      <Slide class="bg-green-100" :index="1">2</Slide>
      <Slide class="bg-green-100" :index="2">3</Slide>
      <Slide class="bg-green-100" :index="3">4</Slide>
      <Slide class="bg-green-100" :index="4">5</Slide>
      <Slide class="bg-green-100" :index="5">6</Slide>
    </Carousel>
  </div>
</template>

<script setup>
import Carousel from './components/Carousel.vue'
import Slide from './components/Slide.vue'
</script>

<style scoped></style>
