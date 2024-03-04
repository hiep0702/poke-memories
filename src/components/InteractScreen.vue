<template>
  <div class="screen">
    <card-flip
      v-for="(card, index) in cardsContext"
      :key="index"
      :imgBackFaceUrl="`images/${card}.png`"
      :card="card"
      @onFlip="checkRule($event)"
    />
  </div>
</template>

<script>
import CardFlip from "./CardComponent.vue";

export default {
  props: {
    cardsContext: {
      type: Array,
      default: function () {
        return [];
      },
    },
  },
  components: {
    CardFlip,
  },
  data() {
    return {
      rules: [],
    };
  },
  methods: {
    checkRule(card) {
      if (this.rules.length === 2) return false;

      this.rules.push(card);

      if (this.rules.length === 2 && this.rules[0] === this.rules[1]) {
        console.log("right...");
      } else if (this.rules.length === 2 && this.rules[0] !== this.rules[1]) {
        console.log("wrong...");
      } else return false;
    },
  },
};
</script>
