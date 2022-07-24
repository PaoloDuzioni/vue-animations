<script setup>
import AppButton from './AppButton.vue';
import FadeTransition from '@/components/transitions/FadeTransition.vue';

// Props
defineProps({
    isOpen: {
        type: Boolean,
        default: false,
    },
});
</script>

<template>
    <FadeTransition>
        <div v-show="isOpen" class="modal">
            <div class="contents">
                <h2>This is a modal Title</h2>
                <p>
                    Lorem ipsum dolor sit amet consectetur adipisicing elit.
                    Distinctio perspiciatis, pariatur autem, quibusdam sed id
                    quidem neque, consectetur quas veritatis hic fugit officia?
                    Accusamus eos unde doloribus, eligendi quaerat aspernatur.
                </p>
            </div>
            <AppButton @clicked="$emit('close')">Close</AppButton>
        </div>
    </FadeTransition>
</template>

<style scoped>
.modal {
    position: fixed;
    top: 0;
    left: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;
    background-image: linear-gradient(
        45deg,
        var(--primary),
        var(--secondary),
        var(--tertiary)
    );
}

.contents {
    margin: 3rem;
    background: rgba(255, 255, 255, 0.25);
}
</style>
