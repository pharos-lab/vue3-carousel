<template>
    <div class="pl-carousel-slide h-56" v-show="visibles">
        <slot></slot>
    </div>
</template>

<script setup>
import { inject, computed, onMounted } from 'vue'

const currentSlide = inject('currentSlide')

const props = defineProps({
    index: Number
})

const visibles = computed(() => {
    //console.log(props)
    return props.index == currentSlide.value
})
</script>