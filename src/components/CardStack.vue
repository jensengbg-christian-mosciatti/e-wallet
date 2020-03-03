<template>
  <section class="card-stack">
    <section class="card-cont">
      <Card
        class="cards"
        v-for="(card, index) in cards"
        :key="card.id"
        :index="index"
        :card="card"
        @click.native="pickCard(card.id)"
      />
    </section>

    <div class="btn-cont">
      <button class="btn btn-primary" @click="addCard">ADD A NEW CARD</button>
    </div>
  </section>
</template>

<script>
import Card from "./Card.vue";
export default {
  components: {
    Card
  },
  props: {
    cards: Array
  },
  methods: {
    pickCard(cardId) {
      this.$emit("pickCard", cardId);
    },
    addCard() {
      this.$router.push("addcard");
    }
  }
};
</script>

<style scoped>
.cards {
  margin-bottom: -12em;
  transform-origin: 100% 100%;
  transition: transform 1s;
}
.cards:hover,
.cards:focus {
  transform: rotateZ(5deg);
}

.card-cont {
  padding-bottom: 200px;
}
.btn-cont {
  width: 100%;
  margin-top: 1rem;
}
.btn {
  margin: 0.2rem;
  cursor: pointer;
  font-family: "PT Mono", sans-serif;
  font-size: 1.1em;
  font-weight: bold;
  width: 98%;
  border: 2px solid rgb(44, 44, 44);
  border-radius: 5px;
  height: 3rem;
}

.btn-primary {
  background-color: rgb(44, 44, 44);
  color: white;
}
</style>
