<template>
    <main>
        <div class="contain">
            <section>
                <FilterCards @mostra="archetypeFilter" />
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
        apiObject(genericUrl) {
            axios.get(genericUrl)
                .then(risposta => {
                    let array = [];
                    this.store.arrayObject = array;
                    risposta.data.data.forEach(element => {
                        this.store.arrayObject.push(element);
                        //console.log(element.archetype)
                    });
                });
        },

        archetypeFilter(value) {
            console.log(value);
            if (value === "tutti") {
                this.apiObject(this.url);
            }
            else {
                //CAMBIO IL MIO URL
                let filtro = this.url + "&archetype=" + value;
                console.log(filtro);

                this.apiObject(filtro);
            }
        },
    },
    components: {
        Cards,
        FilterCards,
    },
    created() {
        this.apiObject(this.url);
    },
    updated() {
        this.archetypeFilter(value);
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