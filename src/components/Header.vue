<template>
    <header>
        <div class="title">
            <a href="/">
                <img
                    src="https://fontmeme.com/permalink/210512/fa6f6e4f4884ea9a87e29bf7ec440b62.png"
                    alt=""
            /></a>
        </div>
        <div class="search">
            <input
                v-on:keyup.enter="$emit('performSearch', search)"
                type="text"
                placeholder="Inserisci titolo"
                v-model="search"
            />
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
    background-color: #080808d2;
    margin-bottom: 30px;
    width: 99%;
    outline: none;
    transform: translate(-13px, -10px);
    position: fixed;
    z-index: 1;
    img {
        padding-left: 20px;
    }
    label {
        width: 50%;
    }
    input {
        display: flex;
        padding: 10px;
        margin-right: 20px;
        background-color: white;
        border: 2px solid black;
        color: #111;
        font-size: 15px;
        box-shadow: 3px 1px 0px 2px, 0px -1px 0px 2px rgba(0, 0, 0, 0.62);
        transform: skew(-3deg, 1deg);
        font-family: 'Knewave', cursive;
        letter-spacing: 2px;
        text-transform: uppercase;
        &:focus,
        &:valid {
            outline: none;
            ~ ul li {
                @for $i from 1 through 6 {
                    &:nth-child(#{$i}) {
                        &::before {
                            filter: blur(20px);
                            transform: translate(0, -35px) rotate(-210deg);
                        }
                        &::after {
                            filter: blur(0);
                            transform: scale(1) rotate(0);
                        }
                    }
                }
                @for $i from 1 through 6 {
                    &:nth-child(#{$i}) {
                        &::after {
                            transition-delay: 200ms + ($i * 200ms);
                        }
                    }
                }
            }
        }
    }
}
</style>
