<template>
    <section class="pl-carousel relative overflow-hidden">
        <slot></slot>

        <div @click="prev" v-if="props.arrows" class="pl-carousel-prev-slide absolute left-0 top-0 h-full w-16 flex items-center justify-center">
            <ChevronLeftIcon class="w-7 h-7"></ChevronLeftIcon>
        </div>
        <div @click="next" v-if="props.arrows" class="pl-carousel-next-slide absolute right-0 top-0 h-full w-16 flex items-center justify-center">
            <ChevronRightIcon class="w-7 h-7"></ChevronRightIcon>
        </div>
    </section>
</template>

<script setup>
import { ref, useSlots, provide, } from 'vue'
import { ChevronRightIcon, ChevronLeftIcon } from '@heroicons/vue/24/solid'


const props = defineProps({
    arrows: {
        type: Boolean,
        default: true
    }
})
const currentSlide = ref(0)
const direction = ref()
const slots = useSlots().default()

provide('currentSlide', currentSlide)
provide('direction', direction)

function prev() {
    direction.value = 'left'
    currentSlide.value == 0 ? currentSlide.value = slots.length - 1 : currentSlide.value--
}

function next() {
    direction.value = 'right'
    currentSlide.value == slots.length - 1  ? currentSlide.value = 0 : currentSlide.value++
}

</script>