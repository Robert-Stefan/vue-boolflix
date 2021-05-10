<template>
    <div id="app">
        <Header />
        <Content />
    </div>
</template>

<script>
import Header from '@/components/Header.vue';
import Content from '@/components/Content.vue';

export default {
    name: 'App',
    components: {
        Header,
        Content,
    },
};
</script>

<style lang="scss">
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

body {
    font-family: sans-serif;
}
</style>
