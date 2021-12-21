<template>
    <div id="film-card">
        <img v-if="img != null" :src="http+img" alt="">
        <div id="informazioni">
            <h4><span>Titolo: </span>{{titolo}}</h4>
            <h4><span>Titolo originale: </span>{{titoloOriginale}}</h4>
            <h5 v-if="overview != ''" id="overview"><span>Overview: </span>{{overview}}</h5>
            <h5>{{lingua }} <lang-flag :iso='lingua'/></h5>
            <div id="vote">
                <h5>
                    <span>Voto: </span>
                    {{stelle = Math.ceil(voto / 2)}} 
                    <i class="colored" v-for="(stella,index) in stelle" :key="index">
                        &#9733;
                </i>
                </h5>
                <h5>
                    <i class="no-color" v-for="stellina in 5 - Math.ceil(voto / 2)" :key="stellina">
                        &#9733;
                    </i>
                </h5>
            </div>
        </div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    name: "FilmCard",
    components: {
        LangFlag
    },
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
        http: String,
        overview: String
    }
}
</script>

<style lang="scss" scoped>
    #film-card {
        width: 250px;
        height: 375px;
        border-radius: 1rem;
        background-color: rgba(0, 0, 0, 0.75);
        margin: 10px;
        padding: 10px;
        border: 1px solid white;
        text-align: center;
        position: relative;
        overflow-y: hidden;
        &:hover img {
            opacity: 0;
        }
        img {
            width: 100%;
            height: 100%;
            border-radius: 1rem;
            position: absolute;
            top: 0;
            left: 0;
            z-index: 9999;
            border: none;
        }
        #informazioni {
            span {
                text-transform: uppercase;
            }
            color: white;
            &> * {
                margin-top: 10px;
            }
            &h5 {
                z-index: -1;
            }
            #overview {
                font-size: 10px;
            }
            #vote {
                display: flex;
                justify-content: center;
                align-items: center;
                h5 {
                margin-right: 5px;
                i.colored {
                    color: goldenrod;
                    }
                }
            }
        }
    }
</style>