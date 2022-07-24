<script setup>
import CloseIcon from './Icons/CloseIcon.vue';
defineProps({
    text: {
        type: String,
        required: true,
    },
});
</script>

<template>
    <li>
        <span class="text">{{ text }}</span>
        <CloseIcon class="close" @click="$emit('remove')" />
    </li>
</template>

<style scoped>
li {
    display: flex;
    margin: 0 0 2rem;
    padding-top: 2rem;
    border-top: 1px solid var(--primary);
}
li:first-child {
    border-top: none;
}
.text {
    flex-grow: 1;
    text-align: left;
}
.close {
    fill: var(--secondary);
    width: 1.5rem;
    cursor: pointer;
}
</style>
