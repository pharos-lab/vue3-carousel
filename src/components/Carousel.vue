<template>
    <section class="pl-carousel relative">
        <slot></slot>

        <div @click="prev" class="pl-carousel-prev-slide absolute left-0 h-full w-20 flex items-center justify-center">
            <ChevronLeftIcon class="w-7 h-7"></ChevronLeftIcon>
        </div>
        <div class="pl-carousel-next-slide absolute right-0 h-full w-20 flex items-center justify-center">
            <ChevronRightIcon class="w-7 h-7"></ChevronRightIcon>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted, useSlots, provide } from 'vue'
import { ChevronRightIcon, ChevronLeftIcon } from '@heroicons/vue/24/solid'

const currentSlide = ref(0)
const slots = useSlots()

provide('currentSlide', currentSlide)

function prev() {
    currentSlide.value++
}
</script>