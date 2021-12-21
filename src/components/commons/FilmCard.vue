<template>
    <div id="film-card">
        <h3>{{titolo}}</h3>
        <h3>{{titoloOriginale}}</h3>
        <h4>{{lingua}}</h4>
        <h4>{{voto}}</h4>
    </div>
</template>

<script>
export default {
    name: "FilmCard",
    props: {
        titolo: String,
        titoloOriginale: String,
        lingua: String,
        voto: Number
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