<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      //   console.log(this.delay);
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      // console.log(this.reactionTime);
      this.$emit('sendReactionTime', this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 40rem;
  border-radius: 2rem;
  background: #d3eca7;
  color: #fff;
  text-align: center;
  padding: 10rem 0;
  margin: 4rem auto;
}
</style>
