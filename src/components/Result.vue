<template>

  <p >Reactio time : {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>

</template>

<script>
export default {
    props : ['score'],
    data(){
        return {
            rank:null
        }
    },
    mounted(){
        if (this.score < 250){
            this.rank = 'ninja fingers '
        }else if (this.score < 350){
            this.rank = 'Rapid reflexes'
        }else{
            this.rank = 'Snail pace'
        }
    }
}
</script>


<style>
    .rank{
        font-size: 1.4rem;
        color: #0faf87;
        font-weight: bold;
    }
</style>