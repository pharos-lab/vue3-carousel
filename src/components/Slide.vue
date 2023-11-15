<template>
    <div class="pl-carousel-slide h-56" v-show="visible">
        <slot></slot>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const index = ref(0)

const props = defineProps({
    visible: {
        type: Boolean,
        default: false
    }
})

</script>