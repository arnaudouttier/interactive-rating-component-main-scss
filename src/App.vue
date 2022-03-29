<template>
  <main>
  <Card/>
  </main>
</template>

<script>
import Card from './components/Card.vue'

export default {
  name: 'App',
  components: {
    Card
  }
}
</script>

<style lang="scss">
@import "@/assets/scss/_global.scss";
#app{
  width: 100vw;
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
