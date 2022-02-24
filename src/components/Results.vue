<template>
  <div class="result">
    <p>Your reaction time is {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
  </div>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = 'Wow, you have fast fingers';
    } else if (this.score < 400) {
      this.rank = 'Rapid Reflexes';
    } else {
      this.rank = 'Snail pace ...';
    }
  },
};
</script>

<style>
.result {
  margin-top: 1rem;
}
.rank {
  font-size: 1.4em;
  color: #3f6272;
  font-weight: 700;
}
</style>
