<template>
  <div>
    <p>Reaction time: {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Ninja reaction";
    } else if (this.score < 400) {
      this.rank = "not bad";
    } else {
      this.rank = "turtle";
    }
  },
};
</script>

<style>
.rank {
  font-size: 1.4rem;
  color: rgb(24, 124, 91);
  font-weight: bold;
}
</style>
