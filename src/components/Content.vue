<template>
    <div class="lista">
        <ul v-for="(film, i) in films" :key="i">
            <li>
                <div class="covers">
                    <div v-if="film.backdrop_path === null">
                        <img
                            class="image"
                            src="@/assets/no-poster.png"
                            alt=""
                        />
                    </div>
                    <div v-else>
                        <img
                            class="image"
                            :src="
                                `https://image.tmdb.org/t/p/w220_and_h330_face/${film.poster_path}`
                            "
                            alt=""
                        />
                    </div>
                    <div class="text">
                        <div v-if="film.title === undefined">
                            Titolo: {{ film.name }}
                        </div>
                        <div v-else>Titolo: {{ film.title }}</div>
                        <div v-if="film.original_title === undefined">
                            Titolo originale: {{ film.original_name }}
                        </div>
                        <div v-else>
                            Titolo originale: {{ film.original_title }}
                        </div>
                        <div v-if="film.original_language === 'it'">
                            Lingua:
                            <img class="flag" src="@/assets/it.png" alt="it" />
                        </div>
                        <div v-else-if="film.original_language === 'en'">
                            Lingua:
                            <img class="flag" src="@/assets/en.png" alt="en" />
                        </div>
                        <div v-else>Lingua: {{ film.original_language }}</div>
                        <div>
                            Voto:
                            <span
                                v-for="(blackStar, i) in Math.round(
                                    film.vote_average / 2
                                )"
                                :key="'A' + i"
                                ><i class="fas fa-star"></i
                            ></span>
                            <span
                                v-for="(whiteStar, i) in 5 -
                                    Math.round(film.vote_average / 2)"
                                :key="'B' + i"
                                ><i class="far fa-star"></i
                            ></span>
                        </div>
                        <div>Informations: {{ film.overview }}</div>
                    </div>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Content',
    props: ['films'],
};
</script>

<style lang="scss" scoped>
.flag {
    width: 40px;
    height: 20px;
    padding-left: 10px;
}

.lista {
    display: flex;
    flex-wrap: wrap;
    margin: 0 50px;
    padding-top: 150px;
    ul {
        list-style: none;
        margin: 10px 10px;

        .covers {
            position: relative;
            cursor: pointer;
            &:hover .text {
                display: flex;
            }
            .image {
                width: 290px;
                height: 450px;
                border-radius: 5px;
            }

            .text {
                flex-direction: column;
                position: absolute;
                background-color: rgba(0, 0, 0, 0.7);
                top: 0;
                left: 0;
                right: 0;
                bottom: 3px;
                padding: 15px;
                border-radius: 5px;
                color: #fff;
                overflow: auto;
                display: none;
                div {
                    padding-bottom: 10px;
                    i {
                        color: #fff;
                    }
                }
            }
        }
    }
}
</style>
