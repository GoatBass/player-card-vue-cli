<template>
  <div v-if="notYetFlippedCards">
    <poker-card
      @flipped-card="managedFlippedCard"
      :message="message"
      v-for="card in deck"
      :card-image="card.url"
      :card-name="card.name"
      :key="card.name"
    ></poker-card>
  </div>
  <div v-else>
    <h2>{{ message }}</h2>
    <poker-card-static v-for="card in flippedCards" :key="card.name" :card-image="card.cardImage"></poker-card-static>
  </div>
</template>

<script>
import PokerCard from "./PokerCard.vue";
import PokerCardStatic from "./PokerCardStatic.vue";


export default {
  components: {
    PokerCard,
    PokerCardStatic,
  },
  data() {
    return {
      suits: ["spades", "clubs", "hearts", "diamonds"],
      numbers: [
        "2",
        "3",
        "4",
        "5",
        "6",
        "7",
        "8",
        "9",
        "10",
        "jack",
        "queen",
        "king",
        "ace",
      ],
      deck: [],
      flippedCards: [],
      message: "",
    };
  },
  beforeMount() {
    this.generateDeck();
    this.shuffleDeck(this.deck);
    this.deck = this.deck.slice(0, 10);
  },
  computed: {
      notYetFlippedCards(){
          return this.flippedCards.length != 5
      }
  },
  methods: {
    generateDeck() {
      const deck = [];
      for (const suit in this.suits) {
        for (const number in this.numbers) {
          deck.push({
            number: this.numbers[number],
            suit: this.suits[suit],
            name: this.numbers[number] + this.suits[suit],
            url:
              "/png/" +
              this.numbers[number] +
              "_of_" +
              this.suits[suit] +
              ".png",
          });
        }
      }
      this.deck = deck;
    },
    shuffleDeck(deck) {
      deck.sort(() => Math.random() - 0.5);
    },
    managedFlippedCard(card) {
      this.flippedCards.push(card);
      if (this.flippedCards.length == 5) {
        this.message = "Ya has girado 5 cartas";
        return;
      }
      console.log("Carta recibida: ", card.cardName);
    },
  },
};
</script>