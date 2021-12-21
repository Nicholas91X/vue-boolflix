<template>
    <main>
        <h2 v-if="film.length > 0">Films</h2>
        <section>
            <FilmCard v-for="(movie,index) in film" :key="index" :http="indirizzo" :img="film[index].poster_path" :titolo="film[index].title" :titoloOriginale="film[index].original_title" :lingua="film[index].original_language" :voto="film[index].vote_average" :overview="film[index].overview"/>
        </section>
        <h2 v-if="serie.length > 0">Serie tv</h2>
        <section>
            <FilmCard v-for="(movie,index) in serie" :key="index" :http="indirizzo" :img="serie[index].poster_path" :titolo="serie[index].name" :titoloOriginale="serie[index].original_name" :lingua="serie[index].original_language" :voto="serie[index].vote_average" :overview="serie[index].overview"/>
        </section>
        <h2 v-if="serie.length == 0 && film.length == 0">Trending</h2>
        <section v-if="serie.length == 0 && film.length == 0">
            <FilmCard v-for="(movie,index) in trend" :key="index" :http="indirizzo" :img="trend[index].poster_path" :titolo="trend[index].title" :titoloOriginale="trend[index].original_title" :lingua="trend[index].original_language" :voto="trend[index].vote_average" :overview="trend[index].overview"/>
        </section>
    </main>
</template>

<script>
import FilmCard from "../commons/FilmCard.vue"
export default {
    name: "Main",
    data() {
        return {
            indirizzo: "https://image.tmdb.org/t/p/w342"
        }
    },
    props: {
        film: Array,
        serie: Array,
        trend: Array
    },
    components: {
        FilmCard
    }
}
</script>

<style lang="scss" scoped>
    main {
        background-color: rgba(0, 0, 0, 0.5);
    }
    section {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
    }
    h2 {
        text-align: center;
        text-transform: uppercase;
        padding: 20px;
        color: white;
    }
</style>