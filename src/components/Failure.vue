<template>
  <div class="container">
    <h2>Failure!</h2>
  <button @click="newGame">New Game</button>
  </div>
</template>

<script>
  export default{
    methods:{
      newGame(){
        this.$emit("isCorrectComponent",'app-game-cards')
      }
    }
  }
</script>

<style scoped>
  .container{
    width: 100vw;
    height: 100vh;
    display: flex;
    background: rgb(152, 1, 1);
    color: #fff;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    position: absolute;
    top: 0;
    left: 0;
  }
  button{
    font-size: 24px;
    letter-spacing: 3.2px;
  }
</style>