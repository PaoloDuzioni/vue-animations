<script setup>
defineProps({
    speed: {
        type: [String, Number],
        default: 300,
    },
});
</script>

<template>
    <Transition name="fade" class="fade" :style="`--speed: ${speed}ms`">
        <slot></slot>
    </Transition>
</template>

<style>
/* Note: avoid using <style scoped> here since it
  does not apply to slot content. */
.fade {
    --speed: 300ms;
}
.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
.fade-enter-active,
.fade-leave-active {
    transition: opacity var(--speed) ease-out;
}
</style>
