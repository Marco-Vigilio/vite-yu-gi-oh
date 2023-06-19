<template>
    <div class="contain">
        <div class="found">Found</div>
        <div class="cards">
            <Card v-for="element in store.arrayObject" :image=element.card_images[0].image_url :name=element.name
                :archetype=element.archetype />
        </div>
    </div>
</template>
<script>
import Card from './Card.vue';
import { store } from '../store.js';
export default {
    name: "",
    components: {
        Card,
    },
    data() {
        return {
            store
        }
    },
}
</script>
<style lang="scss" scoped>
.contain {
    background-color: white;
    padding: 1rem;
}

.found {
    background-color: #212529;
    padding: 1rem;
    color: white;
}

.cards {
    background-color: white;
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
}
</style>