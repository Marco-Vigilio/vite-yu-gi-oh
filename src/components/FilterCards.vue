<template>
    <div class="filter">
        <!--
        <select name="name" id="name" @change="mioMetodo(), $emit('mostra', valore)">
            <option value="Tutti">Tutti</option>
            <option value="Op1">Op1</option>
            <option value="Op2">Op2</option>
        </select>
-->
        <select name="filtro" id="filtro" v-model="archetypeName" @change="$emit('mostra', archetypeName)">
            <option value="tutti">Tutti</option>
            <option :value="element" v-for="element in store.arrayObjectArchetypeName">
                {{ element }}
            </option>
        </select>
    </div>
</template>
<script>
import { store } from '../store.js';
export default {
    name: "FilterCards",
    data() {
        return {
            archetypeName: "",
            store,
        }
    },
    methods: {
        //@change="$emit('mostra', value)"

        apiArchetypesList() {
            axios.get("https://db.ygoprodeck.com/api/v7/archetypes.php")
                .then(risposta => {
                    for (let index = 0; index < 15; index++) {
                        this.archetypeName = risposta.data[index].archetype_name;
                        this.store.arrayObjectArchetypeName.push(risposta.data[index].archetype_name);
                    }

                });
        },

        saveVariables() {
            this.archetypeName = store.archetype;
        },
    },

    created() {
        this.saveVariables();
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