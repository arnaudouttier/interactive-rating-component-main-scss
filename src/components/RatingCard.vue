<template>
  <div class="card">
    <div class="raiting-card" v-if="!show">
      <div class="card-icon">
        <svg width="17" height="16" xmlns="http://www.w3.org/2000/svg">
          <path
            d="m9.067.43 1.99 4.031c.112.228.33.386.58.422l4.45.647a.772.772 0 0 1 .427 1.316l-3.22 3.138a.773.773 0 0 0-.222.683l.76 4.431a.772.772 0 0 1-1.12.813l-3.98-2.092a.773.773 0 0 0-.718 0l-3.98 2.092a.772.772 0 0 1-1.119-.813l.76-4.431a.77.77 0 0 0-.222-.683L.233 6.846A.772.772 0 0 1 .661 5.53l4.449-.647a.772.772 0 0 0 .58-.422L7.68.43a.774.774 0 0 1 1.387 0Z"
            fill="#FC7614"
          />
        </svg>
      </div>
      <h2 class="card-title">How did we do?</h2>
      <p class="card-content">
        Please let us know how we did with your support request. All feedback is
        appreciated to help us improve our offering!
      </p>
      <div class="card-raiting">
        <button
          v-for="n in 5"
          :key="n"
          class="raiting-btn"
          :value="n"
          @click="getCurrentRaiting(n)"
        >
          {{ n }}
        </button>
      </div>
      <button @click="show = !show" class="card-submit">Submit</button>
      {{ crRaiting }}
    </div>
    <Transition name="slide-fade">
      <div class="result-card" v-if="show">
        <ResultCard :currentRaiting="crRaiting" />
      </div>
    </Transition>
  </div>
</template>

<script>
import ResultCard from './ResultCard.vue'
export default {
  name: 'RatingCard',
  components: {
    ResultCard
  },
  data () {
    return {
      crRaiting: null,
      show: false
    }
  },
  methods: {
    getCurrentRaiting (n) {
      this.crRaiting = n
    }
  }
}
</script>

<style scoped lang="scss">
.card {
  border: 2px solid red;
  color: $Medium_Grey;
  margin: 0 $card_margin;
  padding: $card_padding;
}

.card-icon,
.card-title,
.card-raiting {
  margin-bottom: $margin_md;
}

.card-content {
  margin-bottom: $margin_xxl;
}

.card-submit {
  margin-bottom: $margin_sm;
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
