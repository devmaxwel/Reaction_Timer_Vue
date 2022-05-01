<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>


export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      reactionTime: 0,
      timer:null
    };
  },
  methods: {
    startTimer() {
        this.timer = setInterval(() =>{this.reactionTime +=10},10)
    },
    stopTimer() {
        clearInterval(this.timer)
        console.log(this.reactionTime)
        this.$emit('stop', this.reactionTime)
    },
  },

  //   Vue js life cycle hooks
  // {mounted,updated,created,unmounted, beforeMounted,beforeUpdate, beforeCreated, beforeUnmounted}
  mounted() {
    console.log(" component Mounted");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
      console.log(this.delay);
    }, this.delay);
  },
};

</script>

<style>
.block {
  width: 400px;
  border-radius: 24px;
  background: #ed565b;
  color: #fff;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>