<template>
    <header>
        <div>
            <img src="https://vignette1.wikia.nocookie.net/yugiohenespanol/images/a/aa/Yugioh_anime_logo.jpg/revision/latest?cb=20130310042737&path-prefix=es"
                alt="Yu-Gi-Oh! Logo">
            <h1>Yu-Gi-Oh! Api</h1>
        </div>

    </header>
</template>
<script>
export default {
    name: "Header",
    data() {

    },
}
</script>
<style lang="scss" scoped>
div {
    display: flex;
    font-family: Verdana, Geneva, Tahoma, sans-serif;

    img {
        width: 5%;
        object-fit: contain;
        margin: 0 2rem;
    }
}
</style>