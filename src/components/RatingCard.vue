<template>
  <div class="card-rating">
    <div class="card-icon btn circle-btn">
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
    <div class="rating-buttons">
      <button
        v-for="n in 5"
        :key="n"
        class="btn circle-btn"
        :value="n"
        @click="
          getCurrentRating(n);
          ActiveCurrentRating($event);
        "
      >
        {{ n }}
      </button>
    </div>
    <button @click="toggleShow()" class="card-submit btn orange-btn">
      Submit
    </button>
  </div>
</template>

<script>
export default {
  name: 'RatingCard',
  data () {
    return {
      show: false
    }
  },
  methods: {
    getCurrentRating (n) {
      this.$emit('crScore', n)
    },
    toggleShow () {
      this.$emit('show', false)
    },
    ActiveCurrentRating (event) {
      document
        .querySelectorAll('.card-rating button')
        .forEach((ratingButton) => {
          ratingButton.classList.remove('active')
        })
      event.target.classList.toggle('active')
    }
  }
}
</script>

<style  lang="scss">
.card-rating {
  .card-icon {
    &:hover {
      background-color: $Grey_blue !important;
    }
  }
}

.card-icon,
.card-title {
  margin-bottom: $margin_md;
  font-weight: 700;
}

.card-title {
  font-size: clamp(2.5rem, 5vw, 3rem);
  color: $White;
}

.card-content {
  margin-bottom: $margin_xxl;
  font-size: clamp(1rem, 5vw, 1.5rem);
  line-height: 2;
}

.rating-buttons {
  display: flex;
  justify-content: space-around;
  margin-bottom: $margin_lg;
}

.card-submit {
  margin-bottom: $margin_sm;
}
</style>
