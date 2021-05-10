<template>
    <header>
        <div class="title">
            <h1>BoolFlix</h1>
        </div>
        <div class="search">
            <input
                type="text"
                placeholder="Inserisci titolo"
                v-model="search"
            />
            <button @click="$emit('performSearch', search)">Cerca</button>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            search: '',
        };
    },
};
</script>

<style scoped lang="scss">
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
    background-color: blueviolet;
    margin-bottom: 30px;
    input {
        outline: none;
    }
}
</style>
