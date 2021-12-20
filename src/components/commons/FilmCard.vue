<template>
    <div id="film-card">
        <h2>{{film.title}}</h2>
        <h2>{{film.original_title}}</h2>
        <h3>{{film.original_language}}</h3>
        <h3>{{film.vote_average}}</h3>
    </div>
</template>

<script>
export default {
    name: "FilmCard",
    props: {
        film: Object
    }
}
</script>

<style lang="scss" scoped>
    #film-card {
        width: 200px;
        height: 300px;
        background-color: aqua;
        margin: 10px;
        text-align: center;
    }
</style>