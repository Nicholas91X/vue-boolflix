<template>
    <div>
        <input type="text" placeholder="Cerca film" v-model="stringaRicerca">
        <button @click="$emit('search',stringaRicerca)">Cerca</button>
    </div>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            stringaRicerca: "",
            arrayFilm: [],
            arraySerie: []
        }
    }
}
</script>

<style lang="scss" scoped>

</style>