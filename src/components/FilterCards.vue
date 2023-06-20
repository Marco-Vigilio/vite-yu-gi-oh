<template>
    <div class="filter">
        <select name="name" id="name" @change="mioMetodo(), $emit('mostra', valore)">
            <option value="Tutti">Tutti</option>
            <option value="Op1">Op1</option>
            <option value="Op2">Op2</option>
        </select>

        <select name="filtro" id="filtro">
            <option value="">Tutti</option>
            <option value="" v-for="element in store.arrayObjectArchetypeName">{{ element }}</option>
        </select>
    </div>
</template>
<script>
import { store } from '../store.js';
export default {
    name: "FilterCards",
    data() {
        return {
            valore: "",
            store,
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

        apiArchetypesList() {
            axios.get("https://db.ygoprodeck.com/api/v7/archetypes.php")
                .then(risposta => {
                    for (let index = 0; index < 5; index++) {
                        this.store.arrayObjectArchetypeName.push(risposta.data[index].archetype_name);
                    }

                });
        },
    },

    created() {
        this.apiArchetypesList();
    }
}
</script>
<style lang="scss" scoped>
.filter {
    border: 2px solid black;
    margin: 0 1rem;
}
</style>