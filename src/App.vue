<template>
  <main>
  <RatingCard/>
  </main>
</template>

<script>
import RatingCard from './components/RatingCard.vue'

export default {
  name: 'App',
  components: {
    RatingCard
  }
}
</script>

<style lang="scss">
@import "@/assets/scss/_global.scss";
#app{
  width: 100%;
  height: 100vh;
  font-family: $primary_font;
  background-color: $Very_Dark_Blue;
}

main{
  display: grid;
  justify-content: center;
  align-items: center;
  height: inherit

};
</style>
