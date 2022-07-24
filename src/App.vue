<script setup>
import { ref } from 'vue';
import AppHeader from './components/AppHeader.vue';
import AppModal from './components/AppModal.vue';
import AppButton from './components/AppButton.vue';
import AppList from './components/AppList.vue';
import AppFooter from './components/AppFooter.vue';

const modalVisible = ref(false);

const toggleModal = () => {
    modalVisible.value = !modalVisible.value;
};
</script>

<template>
    <div class="app">
        <AppHeader />

        <main class="container text-center">
            <AppButton @clicked="toggleModal">See Modal</AppButton>
            <AppModal :isOpen="modalVisible" @close="toggleModal" />

            <AppList title="List of items" />
        </main>

        <AppFooter />
    </div>
</template>

<style>
/* GLOBALS */
:root {
    /* COLORS */
    --text-col: #fff;
    --bg-col: #111;
    --primary: #70ffea;
    --secondary: #8c9eff;
    --tertiary: #ba68c8;
    /* Fonts */
    --main-font: 'Montserrat', sans-serif;
    --weight-normal: 400;
    --weight-bold: 700;
    --weight-very-bold: 900;
}

html {
    font-size: 62.5%; /* 1rem = 10px */
}

*,
*:before,
*:after {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: var(--main-font);
    font-size: 1.6rem;
    color: var(--text-col);
    background-color: var(--bg-col);
}

/* UTILITIES */
.container {
    padding-left: 2rem;
    padding-right: 2rem;
}

.text-center {
    text-align: center;
}

/* APP LAYOUT */
.app {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}
main {
    flex-grow: 1;
}
</style>
