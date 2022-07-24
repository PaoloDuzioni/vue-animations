<script setup>
import { onMounted, ref } from 'vue';
import gsap from 'gsap';
import ListInput from './ListInput.vue';
import ListItem from './ListItem.vue';
import SlideUpTransitionGroup from './transitions/SlideUpTransitionGroup.vue';

// Props
defineProps({
    title: {
        type: String,
        required: false,
    },
});

// Data
const items = ref(['Nina', 'Bea', 'Paolo']);

// On Mounted
onMounted(() => {
    gsap.from('.list-item', {
        duration: 0.3,
        delay: 1,
        opacity: 0,
        x: 50,
        stagger: 0.3,
        onComplete: function () {
            gsap.set(this.targets(), { clearProps: 'all' });
        },
    });
});

// Methods
const addNewItem = item => {
    items.value.push(item);
};

const sortItems = () => {
    items.value.sort();
};

const removeItem = index => {
    items.value.splice(index, 1);
};
</script>

<template>
    <section>
        <h2>{{ title }}</h2>

        <ListInput @addInput="addNewItem" @sort="sortItems" />

        <SlideUpTransitionGroup tag="ul">
            <ListItem
                v-for="(item, index) in items"
                :key="item"
                class="list-item"
                :text="item"
                @remove="removeItem(index)"
            />
        </SlideUpTransitionGroup>
    </section>
</template>

<style scoped>
section {
    max-width: 600px;
    margin: 5rem auto;
}
h2 {
    font-size: 3rem;
    color: var(--primary);
}
ul {
    list-style: none;
    padding: 0;
}
</style>
