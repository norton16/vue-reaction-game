<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click me
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data () {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    // Component mounted & data updated lifecycle hooks
    mounted() {
        // Show green block after delay time
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        // Every 10 ms, reactionTime is increased
        startTimer() {     
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        // Stop reaction timer after click green block
        stopTimer() {
            clearInterval(this.timer)
            //Send reaction time with cusom event
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: lightseagreen;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
        cursor: pointer;
    }
</style>