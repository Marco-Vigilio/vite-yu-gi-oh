<template>
    <main>
        <div class="contain">
            <section>
                <FilterCards @mostra="miaFunzione" />
                <!--@mostra="miaFunzione"-->
            </section>
            <section>
                <Cards />
            </section>
        </div>

    </main>
</template>
<script>
//import { store } from '../store';
import axios from 'axios';
import { store } from '../store.js';
import FilterCards from './filterCards.vue';
import Cards from './Cards.vue';
export default {
    name: "Main",
    data() {
        return {
            url: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=15&offset=0",
            store,
        }
    },
    methods: {
        apiObject() {
            axios.get(this.url)
                .then(risposta => {
                    risposta.data.data.forEach(element => {
                        this.store.arrayObject.push(element);
                    });
                });
        },

        miaFunzione(tagOption) {
            console.log(tagOption.value);
            //CAMBIO IL MIO URL
            let filtro = this.url + tagOption.value;
            console.log(filtro);

            axios.get("https://db.ygoprodeck.com/api/v7/archetypes.php")
                .then(risposta => {
                    risposta.data.data.forEach(element => {
                        console.log(element);
                    });
                });
        }
    },
    components: {
        Cards,
        FilterCards,
    },
    created() {
        this.apiObject();
    },
}

</script>
<style lang="scss" scoped>
main {
    background-color: #d48f38;
    padding-bottom: 1rem;

    .contain {
        max-width: 1000px;
        margin: auto;

        section {
            padding-top: 1rem;
        }
    }
}
</style>