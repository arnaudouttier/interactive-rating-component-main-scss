<template>
  <div class="card">
    <RatingCard @crScore="crScore" @show="toggleShow" v-if="!show" />
    <Transition name="slide-fade">
      <ResultCard :currentRaiting="crRaiting" v-if="show" />
    </Transition>
  </div>
</template>

<script>
import RatingCard from './RatingCard.vue'
import ResultCard from './ResultCard.vue'

export default {
  name: 'Card',
  components: {
    RatingCard,
    ResultCard
  },
  data () {
    return {
      crRaiting: null,
      show: false
    }
  },
  methods: {
    crScore (currentScore) {
      this.crRaiting = currentScore
    },
    toggleShow (value) {
      this.show = !value
    }
  }
}
</script>

<style  lang="scss">
.card {
  width: min(90vw, 350px);
  color: $Light_Grey;
  margin: 0 5vw;
  padding: $card_padding;
  background-color: $Dark_Blue;
  border-radius: 2rem;
}

.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}
</style>
