<template>
  <div id="app">
    <Header @search="ricercaFilm"/>
    <Main :film="arrayFilm" :serie="arraySerie" :trend="arrayDefault"/>
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/macro/Header.vue";
import Main from "./components/macro/Main.vue";
export default {
  name: 'App',
  data() {
    return {
      arrayFilm: [],
      arraySerie: [],
      arrayDefault: []
    }
  },
  created() {
      axios.get('https://api.themoviedb.org/3/trending/all/day', {
                params: {
                    api_key: "1f48677f96ae221c18b9129486cfa03a"
                }
            })
            .then(response => this.arrayDefault = response.data.results)
            .catch(function (error) {
                console.log(error);
            });

  },
  components: {
      Header,
      Main
  },
  methods: {
        ricercaFilm: function (stringaRicerca) {
          if (stringaRicerca != "") {
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: "1f48677f96ae221c18b9129486cfa03a",
                    query: stringaRicerca,
                    language: "it-IT"
                }
            })
            .then(response => this.arrayFilm = response.data.results)
            .catch(function (error) {
                console.log(error);
            });
            console.log(this.arrayFilm);

            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key: "1f48677f96ae221c18b9129486cfa03a",
                    query: stringaRicerca,
                    language: "it-IT"
                }
            })
            .then(response => this.arraySerie = response.data.results)
            .catch(function (error) {
                console.log(error);
            });
            console.log(this.arraySerie);
          }
        }
    }
}
</script>

<style lang="scss">
@import "./assets/global.scss";

</style>
