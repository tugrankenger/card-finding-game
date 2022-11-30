<template>
  <div class="game-area">
    <h1 class="title">Where is the <span>correct</span> card<strong>?</strong></h1>
    <h4 class="description">After the choose your card, click at the closed card</h4>

    <div class="container">
      <app-card v-for="card in cards" :card="card"></app-card>
    </div>
    <div class="container">
      <app-default-card></app-default-card>
    </div>
  </div>
</template>

<script>
  import Card from "./Card.vue"
  import DefaultCard from "../components/DefaultCard.vue"
  export default{
    components:{
      appCard: Card,
      appDefaultCard: DefaultCard
    },
    data(){
      return{
        cards:[
          {id:1, component:"app-cards", image:"/src/assets/card-1.jpg"},
          {id:2, component:"app-cards", image:"/src/assets/card-2.jpg"},
          {id:3, component:"app-cards", image:"/src/assets/card-3.jpg"},
          {id:4, component:"app-cards", image:"/src/assets/card-4.jpg"},
          {id:5, component:"app-cards", image:"/src/assets/card-5.jpg"},
        ]
      }
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