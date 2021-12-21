<template>
    <main>
        <section>
            <h2>Films</h2>
            <FilmCard v-for="(movie,index) in film" :key="index" :titolo="film[index].title" :titoloOriginale="film[index].original_title" :lingua="film[index].original_language" :voto="film[index].vote_average"/>
        </section>
        <section>
            <h2>Serie</h2>
            <FilmCard v-for="(movie,index) in serie" :key="index" :titolo="serie[index].name" :titoloOriginale="serie[index].original_name" :lingua="serie[index].original_language" :voto="serie[index].vote_average"/>
        </section>
    </main>
</template>

<script>
import FilmCard from "../commons/FilmCard.vue"
export default {
    name: "Main",
    props: {
        film: Array,
        serie: Array
    },
    components: {
        FilmCard
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