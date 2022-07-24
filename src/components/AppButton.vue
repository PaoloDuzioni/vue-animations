<script setup>
defineProps({
    leftShadow: {
        type: Boolean,
        default: false,
    },
});
</script>

<template>
    <button :class="{ 'left-shadow': leftShadow }" @click="$emit('clicked')">
        <slot></slot>
    </button>
</template>

<style scoped>
button {
    -webkit-apparence: none;
    text-decoration: none;
    padding: 1.5rem 3rem;
    font-size: 1.6rem;
    color: var(--text-col);
    background-color: transparent;
    border: 1px solid currentColor;
    transition: box-shadow 0.2s;
    cursor: pointer;
}
button:hover,
button:focus {
    box-shadow: 5px 5px 0 currentColor;
}
button.left-shadow:hover,
button.left-shadow:focus {
    box-shadow: -5px 5px 0 currentColor;
}
</style>
