<template>
    <div class="forca">
        <img :src="`https://raw.githubusercontent.com/william-costa/wdev-hangman-game-resources/master/images/hangman/${erros}.svg`"  alt="forca em 0">
    </div>
</template>

<script>
export default {
    name: 'forca',
    props: {
        erros: Number
    }
}
</script>

<style scoped>

.forca img{
    height: 100px;
}
</style>