<template>
  <div class="game-area">
    <h1 class="title">Where is the <span>correct</span> card<strong>?</strong></h1>
    <h4 class="description">After the choose your card, click at the closed card</h4>

    <div class="container">
      <transition-group name="rotate-all" appear> <!--add apper for when page load, show animation-->
        <app-card :class="{ 'shadow': selectedCard == card.id }" @click.native="(selectedCard = card.id)"
          v-for="card in cards" :card="card" :key="card">
        </app-card>
      </transition-group>
    </div>
    <div class="container">
      <transition name="rotate" mode="out-in">
        <component :is="activeCard" :card="answer" @click.native="showCard(answer)">
        </component>
      </transition>
    </div>
  </div>
</template>

<script>
import Card from "./Card.vue"
import DefaultCard from "../components/DefaultCard.vue"
export default {
  components: {
    appCard: Card,
    appDefaultCard: DefaultCard
  },
  data() {
    return {
      selectedCard: null,
      answer: {},
      activeCard: 'app-default-card',
      cards: [
        { id: 1, component: "app-card", image: "/src/assets/card-1.jpg" },
        { id: 2, component: "app-card", image: "/src/assets/card-2.jpg" },
        { id: 3, component: "app-card", image: "/src/assets/card-3.jpg" },
        { id: 4, component: "app-card", image: "/src/assets/card-4.jpg" },
        { id: 5, component: "app-card", image: "/src/assets/card-5.jpg" },
      ]
    }
  },
  created() {
    let answer = Math.ceil(Math.random() * this.cards.length)
    // console.log(answer)
    this.answer = this.cards[answer - 1]
    console.log(this.answer)
  },
  methods: {
    showCard(answer) {
      if (this.selectedCard == null) {
        alert("Please before select a card!")
      } else {
        this.activeCard = answer.component
        setTimeout(() => {
          if (answer.id == this.selectedCard) {
            // alert("You are done!!")
            this.$emit("isCorrectComponent", 'app-celebrate')
          } else {
            // alert("Wrong choice!")
            this.$emit("isCorrectComponent", 'app-failure')
          }
        }, 2000)
      }
    }
  }
}
</script>

<style scoped>
.title span {
  color: rgb(63, 173, 63);
}

.title strong {
  color: rgb(102, 22, 22);
}

.container {
  display: flex;
  align-items: center;
  justify-content: center;
}

.shadow {
  box-shadow: 0px 5px 48px rgb(72, 161, 250) !important;
  /* transition: all .5s; */
}

.rotate-all-enter {}

.rotate-all-enter-active {
  animation: rotate-all ease-in-out 2s forwards;
}

.rotate-all-leave {}

.rotate-all-leave-active {}

@keyframes rotate-all {
  from {
    transform: rotateY(0);
  }

  to {
    transform: rotateY(1080deg);
  }
}

.rotate-enter {}

.rotate-enter-active {
  animation: rotate-in .5s ease-in-out forwards;
}

.rotate-leave {}

.rotate-leave-acitve {
  animation: rotate-out .5s ease-in-out forwards;
}

@keyframes rotate-in {
  from {
    transform: rotateY(90deg);
  }

  to {
    transform: rotateY(0deg);
  }
}

@keyframes rotate-out {
  from {
    transform: rotateY(0deg);
  }

  to {
    transform: rotateY(90deg);
  }
}

/* .bounce-enter-active {
  animation: bounce-in 0.5s;
}
.bounce-leave-active {
  animation: bounce-in 0.5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
} */
</style>