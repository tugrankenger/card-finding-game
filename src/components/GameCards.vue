<template>
  <div class="game-area">
    <h1 class="title">Where is the <span>correct</span> card<strong>?</strong></h1>
    <h4 class="description">After the choose your card, click at the closed card</h4>

    <div class="container">
      <app-card v-for="i in 5"></app-card>
    </div>
    <div class="container">

    </div>
  </div>
</template>

<script>
  import Card from "./Card.vue"
  export default{
    components:{
      appCard: Card
    }
  }
</script>

<style scoped>
  .title span{
    color: rgb(63, 173, 63);
  }
  .title strong{
    color: rgb(102, 22, 22);
  }

  .container{
    display: flex;
    align-items: center;
    justify-content: center;
  }

</style>