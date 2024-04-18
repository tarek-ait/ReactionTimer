<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data(){
        return {
            showBlock : false,
            timer:null,
            reactionTime:0
        }
    },
    mounted(){
        setTimeout(() => {
          this.showBlock=true
          this.startTimer()
        }, this.delay)
    },
    updated(){
      
    },
    unmounted(){
      
    },
    methods: {
        startTimer(){
            this.timer = setInterval(() =>{
                this.reactionTime+=10
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime) // sending the data to the parent component
        }
    }
    }
</script>

<style>


    .block{
        width: 300px;
        border-radius: 15px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>