<template>
    <section class="pl-carousel relative overflow-hidden">
        <slot></slot>

        <div @click="prev" v-if="props.arrows" class="pl-carousel-prev-slide">
            <ChevronLeftIcon class="pl-carousel-prev-slide-arrow"></ChevronLeftIcon>
        </div>
        <div @click="next" v-if="props.arrows" class="pl-carousel-next-slide">
            <ChevronRightIcon class="pl-carousel-next-slide-arrow"></ChevronRightIcon>
        </div>
        <div class="pl-carousel-bullets">
            <button @click="showSlide(n)" v-for="n in slots.length" :key="n"
                class="pl-carousel-bullet"></button>
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
    currentSlide.value == slots.length - 1 ? currentSlide.value = 0 : currentSlide.value++
}

function showSlide(n) {
    currentSlide.value > n - 1 ? direction.value = 'left' : direction.value = 'right'
    currentSlide.value = n - 1
}

</script>

<style scoped>
.pl-carousel {
    position: relative;
    overflow: hidden
}

.pl-carousel-prev-slide,
.pl-carousel-next-slide {
    position: absolute;
    top: 0;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 50px
}

.pl-carousel-prev-slide {
    left: 0
}

.pl-carousel-next-slide {
    right: 0
}

.pl-carousel-bullets {
    position: absolute;
    bottom: 20px;
    display: flex;
    justify-content: center;
    gap: 16px;
    width: 100%;
}

.pl-carousel-bullet {
    height: 20px;
    width: 20px;
    border-radius: 50%;
    background-color: rgba(51, 65, 85, .7)
}
.pl-carousel-prev-slide-arrow, .pl-carousel-next-slide-arrow {
    width: 30px;
    height: 30px;
}
</style>