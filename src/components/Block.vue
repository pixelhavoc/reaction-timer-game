<template>
    <div class="block" v-if="showBlock" v-on:click="stopTimer">
        <p>click me</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    props: ['delay'],

    mounted() {
        console.log("Component Mounted");

        setTimeout(() => {
            this.showBlock = true
            this.startTimer()

        }, this.delay)
        
    },

    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer)
            console.log(this.reactionTime)
            this.$emit('end', this.reactionTime)
        }
    },

}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: green;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;

    }
</style>