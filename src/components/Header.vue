<template>
    <div class="header">
        <h1>BOOLFLIX</h1>
        <div class="search">
            <input
                type="search"
                id="site-search"
                name="netflix"
                aria-label="Search through site content"
            />

            <button>Search</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Header',
};
</script>

<style scoped lang="scss">
.header {
    display: flex;
    justify-content: space-between;
    h1,
    .search {
        padding-top: 20px;
        input {
            outline: none;
        }
    }
}
</style>
