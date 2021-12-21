<template>
    <div id="film-card">
        <img :src="http+img" alt="">
        <div id="informazioni">
            <h3>{{titolo}}</h3>
            <h3>{{titoloOriginale}}</h3>
            <h4>{{lingua}}</h4>
            <h4 id="vote">{{stelle = Math.ceil(voto / 2)}} <i class="colored" v-for="(stella,index) in stelle" :key="index">&#9733;</i><i v-for="stella in 5 - Math.ceil(voto / 2)" :key="stella">&#9734;</i>
            </h4>
        </div>
    </div>
</template>

<script>
export default {
    name: "FilmCard",
    data() {
        return {
            stelle: []
        }
    },
    props: {
        img: String,
        titolo: String,
        titoloOriginale: String,
        lingua: String,
        voto: Number,
        http: String
    },
    mounted() {
        console.log(this.stelle)
    }
}
</script>

<style lang="scss" scoped>
    #film-card {
        width: 200px;
        height: 300px;
        background-color: rgba(0, 0, 0, 0.75);
        margin: 10px;
        text-align: center;
        position: relative;
        &:hover img {
            opacity: 0;
        }
        img {
            width: 100%;
            height: 100%;
            position: absolute;
            top: 0;
            left: 0;
        }
        #informazioni {
            color: white;
            h4 {
                font-size: 24px;
                i.colored {
                    color: goldenrod;
                }
            }
        }
    }
</style>