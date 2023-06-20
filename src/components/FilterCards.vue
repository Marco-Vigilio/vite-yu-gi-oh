<template>
    <div class="filter">
        <select name="name" id="name" @change="mioMetodo(this.value)">
            <option value="Tutti">Tutti</option>
            <option value="Op1">Op1</option>
            <option value="Op2">Op2</option>
        </select>
        <button>Click</button>
    </div>
</template>
<script>
export default {
    name: "FilterCards",
    data() {
        return {

        }
    },
    methods: {
        //@change="$emit('mostra', value)"

        //UN METODO CHE MI RESTITUISCE IL VALUE
        mioMetodo(valore) {
            console.log(valore);
        },
    },
}
</script>
<style lang="scss" scoped>
.filter {
    border: 2px solid black;
    margin: 0 1rem;
}
</style>