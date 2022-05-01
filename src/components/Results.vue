<template>
  <div class="block">
    <p>Your Reaction Time - {{ score }} ms</p>
    <p class="rank">What The timer thinks -You have {{ message }}</p>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      message: null,
    };
  },
  mounted() {
      console.log("component mounted")
    if (this.score < 250) {
      this.message = "Ninja Fingers";
    } else if (this.score < 500) {
      this.message = "Rapid reflexes";
    } else {
      this.message = "Snail pace";
    }
  },
};
</script>

<style>
.rank{
    font-weight: bold;
    background: #fff;
    color: crimson;
    border-radius: 20px;
    padding: 20px 20px;
    margin: auto 5px;
    width: 350px;
    justify-content: center;
    display: flex;
}
</style>