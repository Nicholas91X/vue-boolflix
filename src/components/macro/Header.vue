<template>
    <div>
        <div id="logo">
            <h1>BoolFlix</h1>
        </div>
        <div id="search">
            <input @keyup.enter="$emit('search',stringaRicerca)" type="text" placeholder="Cerca film nel catalogo" v-model="stringaRicerca">
            <button @click="$emit('search',stringaRicerca)">Cerca</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            stringaRicerca: "",
            arrayFilm: [],
            arraySerie: [],
            arrayDefault: []
        }
    }
}
</script>

<style lang="scss" scoped>
    div {
        #logo {
            text-transform: uppercase;
            color: red;
            border: none;
        }
        height: 75px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: black;
        padding: 20px;
        border-bottom: 1px solid white;
        #search {
            border: none;
        }
        #search>input {
            padding: 5px;
            margin-right: 3px;
            border-radius: 5px;
        }
        #search>button {
            padding: 5px 15px;
            border-radius: 5px;
        }
    }
</style>