<template>
    <div class="pl-carousel-slide h-56" v-show="visible">
        <slot></slot>
    </div>
</template>

<script setup>
import { inject, computed, } from 'vue'

const currentSlide = inject('currentSlide')

const props = defineProps({
    index: Number
})

const visible = computed(() => {
    return props.index == currentSlide.value
})
</script>