<template>
    <div class="lista">
        <ul v-for="(film, i) in films" :key="i">
            <li>
                <img
                    class="image"
                    :src="
                        `https://image.tmdb.org/t/p/w220_and_h330_face/${film.backdrop_path}`
                    "
                    alt=""
                />
            </li>
            <div class="text">
                <li v-if="film.title === undefined">Titolo: {{ film.name }}</li>
                <li v-else>Titolo: {{ film.title }}</li>
                <li v-if="film.original_title === undefined">
                    Titolo originale: {{ film.original_name }}
                </li>
                <li v-else>Titolo originale: {{ film.original_title }}</li>
                <li v-if="film.original_language === 'it'" class="language">
                    Lingua:
                    <img class="flag" src="@/assets/it.png" alt="it" />
                </li>
                <li
                    v-else-if="film.original_language === 'en'"
                    class="language"
                >
                    Lingua:
                    <img class="flag" src="@/assets/en.png" alt="en" />
                </li>
                <li v-else>Lingua: {{ film.original_language }}</li>
                <li>
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
                </li>
            </div>
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
    padding-top: 10px;
    padding-left: 5px;
}

.language {
    padding-bottom: 7px;
    display: flex;
    align-items: flex-end;
}

.lista {
    display: flex;
    flex-wrap: wrap;
    .text {
        color: #fff;
        width: 220px;
        background-color: #32323263;
        font-size: 15px;
    }
}

ul li {
    list-style: none;
}
</style>
