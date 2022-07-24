<script setup>
import gsap from 'gsap';

const beforeEnter = el => {
    el.style.opacity = 0;
    el.style.transform = 'scale(0,0)';
};

const enter = (el, done) => {
    gsap.to(el, {
        duration: 1,
        opacity: 1,
        scale: 1,
        ease: 'bounce.out',
        onComplete: done,
    });
};
</script>

<template>
    <Transition appear @before-enter="beforeEnter" @enter="enter" :css="false">
        <h1>Animating Vue</h1>
    </Transition>
</template>

<style scoped>
h1 {
    margin: 0 0 5rem;
    padding: 1rem;
    text-align: center;
    font-weight: var(--weight-very-bold);
    font-size: 8rem;
    color: var(--text-col);
    background: linear-gradient(
        to right,
        var(--primary) 10%,
        var(--secondary),
        var(--tertiary) 90%
    );
    background-clip: text;
    color: transparent;
}
</style>
