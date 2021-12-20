<template>
    <main>
        <input type="text" placeholder="Cerca film" v-model="stringaRicerca">
        <button @click="ricercaFilm">Cerca</button>
        <section>
            <FilmCard v-for="(film,index) in film" :key="index" :film="film"/>
        </section>
    </main>
</template>

<script>
import axios from "axios";
import FilmCard from "../commons/FilmCard.vue"
export default {
    name: "Main",
    data() {
        return {
            stringaRicerca: "",
            film: ""
        }
    },
    components: {
        FilmCard
    },
    methods: {
        ricercaFilm: function () {

            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: "1f48677f96ae221c18b9129486cfa03a",
                    query: this.stringaRicerca
                }
            })
            .then(response => this.film = response.data.results)
            .catch(function (error) {
                console.log(error);
            });
            console.log(this.film);
        }
    }
}
</script>

<style lang="scss" scoped>
    section {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
    }
</style>