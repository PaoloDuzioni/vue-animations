<script setup>
defineProps({
    tag: {
        type: String,
        default: 'span',
    },
    speed: {
        type: [String, Number],
        default: 300,
    },
});
</script>

<template>
    <TransitionGroup
        :tag="tag"
        name="slideup"
        class="slideup"
        :style="`--speed: ${speed}ms`"
    >
        <slot></slot>
    </TransitionGroup>
</template>

<style>
/* Note: avoid using <style scoped> here since it
  does not apply to slot content. */
.slideup {
    --speed: 300ms;
}
.slideup-enter-from {
    opacity: 0;
    transform: translateY(2rem);
}
.slideup-leave-to {
    opacity: 0;
}
.slideup-move,
.slideup-enter-active,
.slideup-leave-active {
    transition: opacity var(--speed) ease-out, transform var(--speed) ease-out;
}
</style>
