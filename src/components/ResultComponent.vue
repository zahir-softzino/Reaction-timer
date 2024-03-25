<template>
  <p>Reaction time: {{  score }} ms</p>  
  <p class="result">Result: {{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
        if(this.score<300){
            this.rank = "Less than 300 very good"
        }
        else if(this.score<600){
            this.rank = "Less than 600 not bad"
        }
        else{
            this.rank = "More than 600 ms poor reaction time"
        }
        
    }
}
</script>

<style>
    .result{
        font-size: 30px;
        color: #388;
        font-weight: bold;
    }

</style>