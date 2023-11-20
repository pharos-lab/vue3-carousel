<template>
    <transition :name="transition">
        <div class="pl-carousel-slide h-56 relative" v-show="visible">
            <slot></slot>
        </div>
    </transition>
</template>

<script setup>
import { inject, computed } from 'vue'

const currentSlide = inject('currentSlide')
const direction = inject('direction')


const props = defineProps({
    index: Number,
    direction: String,
})

const visible = computed(() => {
    return props.index == currentSlide.value
})

const transition = computed(() => {
    return 'slide-' + direction.value
})

</script>

<style scoped>

.slide-left-enter-active {
    animation: slideLeftEnter 1s ease-in-out;
}

.slide-left-leave-active {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    animation: slideLeftLeave 1s ease-in-out;
}

.slide-right-enter-active {
    animation: slideRightEnter 1s ease-in-out;
}

.slide-right-leave-active {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    animation: slideRightLeave 1s ease-in-out;
}


@keyframes slideLeftEnter {
    from {
        transform: translateX(-100%);
    }
    to {
        transform: translateX(0);
    }
}

@keyframes slideLeftLeave {
    from {
        transform: translateX(0);
    }
    to {
        transform: translateX(100%);
    }
}

@keyframes slideRightEnter {
    from {
        transform: translateX(100%);
    }
    to {
        transform: translateX(0);
    }
}

@keyframes slideRightLeave {
    from {
        transform: translateX(0);
    }
    to {
        transform: translateX(-100%);
    }
}
</style>