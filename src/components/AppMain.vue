<template>
    <main>
        <div>
            <h1>Main</h1>
            <Cards />
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
<style lang="scss" scoped></style>