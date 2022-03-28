<template>
  <div class="card">
    <RatingCard  @crScore="crSc($event)" v-if="!show" />
    <Transition name="slide-fade">
      <div class="result-card" v-if="show">
        <ResultCard :currentRaiting="crRaiting" />
      </div>
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
    crSc (currentScore) {
      this.crRaiting = currentScore
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

.card-icon,
.card-title,
.card-raiting {
  margin-bottom: $margin_md;
}

.card-title {
  font-size: clamp(2.5rem, 5vw, 3rem);
  color: $White;
  font-weight: 700;
}

.card-content {
  margin-bottom: $margin_xxl;
  font-size: clamp(1.5rem, 5vw, 1.8rem);
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
