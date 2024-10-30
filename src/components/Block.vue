<template>
<div class="block" v-if="showBlock" @click="stopTimer">
  Click Me
</div>
</template>

<script>

export default {
  props: ['delay'],
  data () {
    return {
      showBlock : false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted () {
    setTimeout(()=> {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer() {
      this.timer=setInterval (()=> {
        this.reactionTime += 10
      },10)
    },
    stopTimer () {
     clearInterval(this.timer)
    this.$emit('end', this.reactionTime)
    }
  }
}

</script>

<style>
.block{
  width:400px;
  padding: 100px;
  margin: 40px auto;
  color: white;
  background-color: aquamarine;
  text-align:  center;
  border-radius: 30px;
}
</style>