<template>
    <div class="card">
        <div class="image">
            <img :src="image" :alt="name + ' image'">
        </div>
        <p class="name">{{ name }}</p>
        <p class="type">{{ archetype }}</p>
    </div>
</template>
<script>
export default {
    name: "",
    data() {
        return {
        }
    },
    props: {
        image: String,
        name: String,
        archetype: String,
    }
}
</script>
<style lang="scss" scoped>
.card {
    background-color: #d48f38;
    width: calc((100% / 5) - 1rem);
    border: 2px solid black;

    .image {
        width: 100%;

        img {
            width: 100%;
            display: block;
        }
    }

    p {
        text-align: center;
    }

    .name {
        color: white;
        text-transform: uppercase;
    }
}
</style>