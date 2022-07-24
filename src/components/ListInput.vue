<script setup>
import { ref } from 'vue';
import AppButton from './AppButton.vue';

const emit = defineEmits(['addInput']);

// Data
const inputValue = ref('');

// Methods
const submitInput = () => {
    if (inputValue.value.length > 0) {
        emit('addInput', inputValue.value);
        inputValue.value = '';
    }
};
</script>

<template>
    <div class="wrap-input">
        <AppButton @clicked="$emit('sort')" left-shadow>Sort Items</AppButton>
        <input
            type="text"
            placeholder="Add new item"
            v-model.trim="inputValue"
            @keyup.enter="submitInput"
        />
        <AppButton @clicked="submitInput">Add</AppButton>
    </div>
</template>

<style scoped>
.wrap-input {
    display: flex;
}
input {
    flex-grow: 1;
    padding: 0 2rem;
    font-size: 1.6rem;
    color: var(--text-col);
    background: transparent;
    border: 1px solid currentColor;
    outline: none;
}
input:hover,
input:focus {
    border-color: var(--tertiary);
}
input::placeholder {
    color: rgba(255, 250, 250, 0.5);
}
</style>
