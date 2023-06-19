<template>
    <div class="contain">
        <div class="found">Found</div>
        <div class="cards">
            <Card />
            <Card />
            <Card />
            <Card />
            <Card />
        </div>
    </div>
</template>
<script>
import Card from './Card.vue';
export default {
    name: "",
    components: {
        Card,
    }
}
</script>
<style lang="scss" scoped>
.contain {
    background-color: white;
    padding: 1rem;
}

.found {
    background-color: #212529;
    width: 100%;
    color: white;
}

.cards {
    background-color: white;
    display: flex;
    justify-content: space-between;
}
</style>