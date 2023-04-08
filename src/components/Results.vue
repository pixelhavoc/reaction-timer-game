<template>
    <div>
        <p>Reaction Time: {{ score }}ms</p>
        <p class="rank">Rank: {{ rank }}</p>
    </div>
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
        if(this.score < 250) {
            this.rank = 'Ninja Fingers'
        }
        else if (this.score < 400) {
            this.rank = 'Rapid Reflexes'
        } else {
            this.rank = 'Snail Pace'
        }
    }
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: green;
        font-weight: bold;
    }
</style>