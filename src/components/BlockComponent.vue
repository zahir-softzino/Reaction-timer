<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click here
  </div>
</template>

<script>
export default {
    props:['delay'],
    data(){
      return{
        showBlock : false,
        timer: null,
        reactionTime: 0,
      }
    },
    mounted(){
      setTimeout(() => {
        this.showBlock = true
        this.startTimer()
      },this.delay)
    },
    methods:{
      startTimer(){
        this.timer = setInterval(() => {
          this.reactionTime += 10
        }, 10);
      },
      stopTimer(){
        clearInterval(this.timer)
        // console.log(this.reactionTime)
        this.$emit('end', this.reactionTime)
      }
    }

}
</script>

<style>
    .block{
        width: 400px;
        /* height: 300px; */
        padding: 100px 0px;
        margin: 40px auto;
        text-align: center;
        color: #DDD;
        background-color: #15A;
        border-radius: 10px;
    }
</style>