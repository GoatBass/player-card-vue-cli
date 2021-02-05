<template>
    <span @click="turnCard">
        <transition name="fade" mode="out-in">
        <img v-if="faceDown" src="../../public/png/back.png" alt="card" width="100" />
        <img v-else :src="cardImage" alt="back-card" width="100" />
        </transition>
    </span>
</template>

<script>
export default {
  name: "PokerCard",
  props: ["cardImage", "cardName"],
  data() {
    return {
      faceDown: true,
    };
  },
  methods: {
    turnCard() {
      this.faceDown = !this.faceDown;
      console.log("The card shown is: ", this.cardName);
    },
  },
};
</script>

<style scoped>
    .fade-enter-active, .fade-leave-active {
    transition: opacity .25s;
}

.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
}
</style>