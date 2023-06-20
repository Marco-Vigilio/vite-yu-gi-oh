<template>
    <div class="filter">
        <select name="name" id="name" @change="mioMetodo(), $emit('mostra', valore)">
            <option value="Tutti">Tutti</option>
            <option value="Op1">Op1</option>
            <option value="Op2">Op2</option>
        </select>
    </div>
</template>
<script>
export default {
    name: "FilterCards",
    data() {
        return {
            valore: "",
        }
    },
    methods: {
        //@change="$emit('mostra', value)"

        //UN METODO CHE MI RESTITUISCE IL VALUE
        mioMetodo() {
            var selectDaVerificare = document.getElementById("name");
            let indiceSelezionato = selectDaVerificare.selectedIndex;
            let valoreSelezionato = selectDaVerificare.options[indiceSelezionato];
            //console.log(valoreSelezionato.value);
            this.valore = valoreSelezionato;
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