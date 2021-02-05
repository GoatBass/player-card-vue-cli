<template>
    <div>
      <PokerCard v-for="card in deck" :card-image="card.url" :card-name="card.name" :key="card.name"></PokerCard>
    </div>
</template>

<script>
import PokerCard from './pokerCard.vue'

export default {
    name: 'PokerGame',
    components: {
        PokerCard
    },
    data(){
        return {
            suits: ['spades', 'clubs', 'hearts', 'diamonds'],
            numbers: ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'jack', 'queen', 'king', 'ace'],
            deck: []
        };
    },
    beforeMount(){
        this.generateDeck();
        this.shuffleDeck(this.deck);
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
                        url: '/png/' + this.numbers[number] + '_of_' + this.suits[suit] + '.png',
                    });
                }
            }
            this.deck = deck;
        },
        shuffleDeck(deck) {
            deck.sort(() => Math.random() - 0.5);
        },
    }
}
</script>