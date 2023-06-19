<template>
    <main>
        <div class="contain">
            <section>
                <select name="name" id="name"></select>
            </section>
            <section>
                <Cards />
            </section>

        </div>

    </main>
</template>
<script>
import Cards from './Cards.vue';
export default {
    name: "Main",
    data() {

    },
    components: {
        Cards,
    }
}
</script>
<style lang="scss" scoped>
main {
    background-color: #d48f38;

    .contain {
        max-width: 1000px;
        margin: auto;

        section {
            padding: 1rem 0;
        }
    }
}
</style>