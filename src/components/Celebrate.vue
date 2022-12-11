<template>
  <div class="container">
    <h2>Celebrate!</h2>
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
    background: #fff;
    color: #333;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    position: absolute;
    top: 0;
    left: 0;
  }
  button{
    background: lightgreen;
    font-size: 24px;
    letter-spacing: 3.2px;
    color: #fff;
  }
  button:hover{
    outline: none;
    border: 1px solid transparent;
    color: #333;
  }
</style>