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
//import { store } from '../store';
import axios from 'axios';
import { store } from '../store.js';
import Cards from './Cards.vue';
export default {
    name: "Main",
    data() {
        return {
            store
        }
    },
    methods: {
        metodo() {
            axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=15&offset=0")
                .then(risposta => {
                    let array = risposta.data;
                    console.log(risposta.data.data);
                    risposta.data.data.forEach(element => {
                        console.log(element.data);
                        this.store.arrayObject.push(element);
                    });
                });
        },
    },
    components: {
        Cards,
    },
    created() {
        this.metodo();
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