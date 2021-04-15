<template>
    <p>Reaction time: {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        this.score < 250 ? this.rank = 'Super fast!' : this.rank = 'Too slow!'
    }
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: lightseagreen;
        font-weight: bold;
    }
</style>