<template>
    <div id="app">
        <Header @performSearch="getFilms" />

        <main>
            <Content :films="film" />
        </main>
    </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue';
import Content from '@/components/Content.vue';
export default {
    name: 'App',
    components: {
        Header,
        Content,
    },
    data() {
        return {
            film: [],
        };
    },
    methods: {
        getFilms(search) {
            Promise.all([
                axios.get(
                    'https://api.themoviedb.org/3/search/movie?api_key=c18dcf0e37553babb7d99593a6f3dc48&language=it-IT&query=' +
                        search
                ),
                axios.get(
                    'https://api.themoviedb.org/3/search/tv?api_key=c18dcf0e37553babb7d99593a6f3dc48&language=it-IT&query=' +
                        search
                ),
            ])
                .then(res => {
                    const film = res[0].data.results;
                    const series = res[1].data.results;
                    let library = [...film, ...series];
                    this.film = library;
                })
                .catch(err => {
                    console.log('Error', err);
                });
        },
    },
};
</script>

<style lang="scss">
body {
    font-family: sans-serif;
}

//Font Awesome
@import url(https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css);
</style>
